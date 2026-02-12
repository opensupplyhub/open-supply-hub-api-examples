# FSearching for Facilities on Open Supply Hub using the /facilities/ endpoint

Search for facilities in the OS Hub database using various filters and criteria.

## When to Use This Endpoint

Use the **Facilities endpoint** (`/api/facilities/`) when you need:

- ✅ **View all contributions to a facility** - See extended details showing every data contribution made to a facility profile
- ✅ **Search by contributor** - Filter facilities by specific contributor IDs or types
- ✅ **Contributor intersection queries** - Find facilities with data from multiple contributors
- ✅ **Parent company filtering** - Search by parent company ownership
- ✅ **Detailed attribution** - See complete contributor information and data provenance

> **📌 Looking for fuzzy search?** The `/api/facilities/` endpoint uses exact matching. For fuzzy search with typo tolerance, geographic search, or address-based search, use the [v1/production-locations/ endpoint](https://github.com/opensupplyhub/open-supply-hub-api-examples/blob/main/how_to/fuzzy_search_guide.md) instead. Note that this endpoint does not support extended details or contributor-based filtering.

---

## Base URL

```
GET https://opensupplyhub.org/api/facilities/
```

---

## Quick Start

Search facility by OS ID:
```
GET /api/facilities/BD2021113R7R87P
```
Returns a facility with all data that has been contributed about that facility; details parameter defaults to true when searching by a single ID.

---

## Search Parameters

### Query Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `detail` | boolean | `false` | **Return extended details showing all contributions made to each facility.** Includes complete contributor information, attribution, and extended fields (custom data attributes). Setting to `true` makes responses significantly longer and slower. **This is the only way to see all data contributions to a facility profile.** |
| `number_of_public_contributors` | boolean | `false` | Include count of public contributors for each facility |
| `combine_contributors` | string | `OR` | How to combine multiple contributor filters. Use `AND` to find facilities with data from all specified contributors |
| `sort_by` | string | `contributors` | Sort results by `contributors` (default, most to least) or `NAME` (alphabetically) |
| `page` | integer | `1` | Page number for paginated results |
| `pageSize` | integer | `50` | Results per page. **Max:** 50 when `detail=false`, 10 when `detail=true` |

### Filter Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `q` | string | Search term for facility name or OS ID |
| `countries` | string | Two-character country code (e.g., `BD`, `US`)|
| `contributors` | integer | **Filter by contributor ID.** This is unique to the Facilities endpoint - Production Locations does not support contributor filtering. Get the full list of IDs from the [/contributors/ endpoint](https://github.com/opensupplyhub/open-supply-hub-api-examples/blob/main/how_to/contributor-search-guide.md)|
| `product_type` | string | Filter by [product type](https://docs.google.com/spreadsheets/d/18ABJuS5CY4cr9JaTzPeLaAr1uhdu7VJXK6JpibP1b1o/edit?gid=0#gid=0)|
| `sector` | string | Filter by [sector](https://docs.google.com/spreadsheets/d/18ABJuS5CY4cr9JaTzPeLaAr1uhdu7VJXK6JpibP1b1o/edit?gid=0#gid=0)|
| `contributor_types` | string | **Filter by contributor type** (e.g., Brand, Multi-Stakeholder Initiative). Unique to Facilities endpoint. Get types from [GET /contributor-types/](../reference/contributor-types.md) |
| `parent_company` | string | Filter by parent company name or contributor ID. Get companies from [GET /parent-companies/](../reference/parent-companies.md) |
| `facility_type` | string | Filter by facility type (e.g., "Final Product Assembly"). Get types from [GET /facility-processing-types/](../reference/facility-processing-types.md) |
| `processing_type` | string | Filter by processing activity (e.g., "Printing", "Cutting"). Get types from [GET /facility-processing-types/](../reference/facility-processing-types.md) |

---

## Response Format

Responses are returned in **GeoJSON format** with the following structure:

### Basic Response (`detail=false`)

```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [longitude, latitude]
      },
      "properties": {
        "os_id": "BD2020123ABC456",
        "name": "Example Textile Factory",
        "address": "123 Industrial Road, Dhaka",
        "country_code": "BD",
        "country_name": "Bangladesh"
      }
    }
  ]
}
```

### Extended Response (`detail=true`)

**This is the only endpoint that provides complete contribution history for facilities.**

Additional fields included when `detail=true`:
- **All contributor information** - See every organization that has contributed data
- **Complete attribution** - Understand data provenance and sources
- **Extended fields** - Custom data attributes submitted by contributors
- **Contribution metadata** - When data was added, by whom, and what was contributed
- **Full facility profile** - All data points aggregated from multiple sources

> **💡 Use Case:** When you need to understand what data each contributor has provided about a facility, or when you need to see the complete history of contributions, set `detail=true`. This is not available in the Production Locations endpoint.

---

## Examples

### Example 1: Basic Text Search

Search for facilities with "textile" in the name:

```bash
GET /api/facilities/?q=textile
```

**Returns:** All facilities matching "textile" in name or OS ID

---

### Example 2: Country Filter

Find all facilities in Bangladesh:

```bash
GET /api/facilities/?countries=BD
```

**Returns:** All Bangladesh facilities (up to 50 per page)

---

### Example 3: Combined Filters

Search for apparel facilities in Bangladesh:

```bash
GET /api/facilities/?sector=Apparel&countries=BD
```

---

### Example 4: View All Contributions to Facilities

Get complete contribution history with detailed attribution:

```bash
GET /api/facilities/?countries=BD&detail=true&pageSize=10
```

**Returns:** Up to 10 facilities with full details showing:
- All contributors who have submitted data
- What each contributor added
- Extended fields and custom attributes
- Complete data provenance

> **⚠️ Important:** The Production Locations endpoint does not support this level of detail. Use Facilities endpoint to see all contributions.

---

### Example 5: Specific Contributor Data

Find facilities uploaded by contributor ID 123:

```bash
GET /api/facilities/?contributors=123
```

**Returns:** Only facilities where contributor 123 has submitted data

> **Note:** Contributor filtering is unique to the Facilities endpoint.

---

### Example 6: Multiple Contributors (Union)

Find facilities from contributor 123 OR contributor 456:

```bash
GET /api/facilities/?contributors=123&contributors=456
```

**Default behavior:** Returns facilities with data from either contributor

---

### Example 7: Multiple Contributors (Intersection)

Find facilities with data from BOTH contributors:

```bash
GET /api/facilities/?contributors=123&contributors=456&combine_contributors=AND
```

**Result:** Only facilities that have data from both contributor 123 AND contributor 456

> **Use Case:** Data verification - find facilities that multiple independent sources have reported on.

---

### Example 8: Filter by Contributor Type

Find facilities reported by brands specifically:

```bash
GET /api/facilities/?contributor_types=Brand
```

**Returns:** Facilities with data from brand contributors

> **Note:** Contributor type filtering is unique to the Facilities endpoint.

---

### Example 9: Facility Type and Processing Type

Find cutting facilities:

```bash
GET /api/facilities/?processing_type=Cutting
```

Find final assembly facilities:

```bash
GET /api/facilities/?facility_type=Final%20Product%20Assembly
```

---

### Example 10: Alphabetical Sorting

Sort results by facility name instead of contributor count:

```bash
GET /api/facilities/?countries=BD&sort_by=NAME
```

---

### Example 11: Parent Company Filter

Find all facilities owned by a specific parent company:

```bash
GET /api/facilities/?parent_company=Acme%20Corporation
```

Or use parent company contributor ID:

```bash
GET /api/facilities/?parent_company=789
```

---

## Pagination

### Default Behavior

- **50 results per page** when `detail=false` or not specified
- **10 results per page** when `detail=true`

### Navigating Pages

Request specific pages using the `page` parameter:

```bash
# First page (default)
GET /api/facilities/?countries=BD&page=1

# Second page
GET /api/facilities/?countries=BD&page=2

# Third page
GET /api/facilities/?countries=BD&page=3
```

### Custom Page Size

Adjust results per page with `pageSize`:

```bash
# 25 results per page
GET /api/facilities/?countries=BD&pageSize=25

# Maximum: 50 (when detail=false)
GET /api/facilities/?countries=BD&pageSize=50

# Maximum: 10 (when detail=true)
GET /api/facilities/?countries=BD&detail=true&pageSize=10
```

### Example: Processing Large Datasets

When working with large result sets, iterate through pages:

```python
page = 1
all_facilities = []

while True:
    response = requests.get(
        "https://opensupplyhub.org/api/facilities/",
        params={
            "countries": "BD",
            "pageSize": 50,
            "page": page
        }
    )
    data = response.json()
    
    if not data["features"]:
        break  # No more results
    
    all_facilities.extend(data["features"])
    page += 1
```

---

## Best Practices

### 1. Use `detail=true` for Data Provenance

When you need to understand all contributions to a facility profile:

✅ **View complete contribution history:**
```bash
GET /api/facilities/?os_id=BD2020123ABC456&detail=true
```

This shows:
- Which contributors have submitted data
- What specific fields each contributor provided
- Extended fields and custom attributes
- Complete data lineage

❌ **Avoid using `detail=true` for:**
- Large-scale data collection (slower, fewer results per page)
- Simple facility lookups (unnecessary overhead)

---

### 2. Search by Contributor for Attribution

Filter by specific contributors to see their data:

```bash
# See all facilities reported by a specific brand
GET /api/facilities/?contributors=123

# See facilities verified by multiple sources
GET /api/facilities/?contributors=123&contributors=456&combine_contributors=AND
```

> **Remember:** Contributor filtering is only available in the Facilities endpoint, not Production Locations.

---

### 3. Use Specific Filters First

Instead of broad searches, combine filters for targeted results:

❌ **Too broad:**
```bash
GET /api/facilities/?q=factory
```

✅ **Better:**
```bash
GET /api/facilities/?q=factory&countries=BD&sector=Apparel
```

---

### 4. Reference Endpoints for Valid Values

Before filtering, retrieve valid values from reference endpoints:

```bash
# Get valid country codes
GET /api/countries/

# Get available sectors
GET /api/sectors/

# Get product types
GET /api/product-types/
```

---

### 5. Sort by Name for Human Review

When reviewing results manually, alphabetical sorting improves readability:

```bash
GET /api/facilities/?countries=BD&sort_by=NAME
```

---

### 6. Count Public Contributors

When analyzing data provenance, include contributor counts:

```bash
GET /api/facilities/?countries=BD&number_of_public_contributors=true
```

---

## Limitations

| Limitation | Value | Notes |
|------------|-------|-------|
| Max results per page (`detail=false`) | 50 | Adjustable with `pageSize` |
| Max results per page (`detail=true`) | 10 | Adjustable with `pageSize` |
| Search matching | Exact | No typo tolerance; use [Production Locations endpoint](./production-locations-search.md) for fuzzy search |
| Country codes | ISO 3166-1 alpha-2 | Two-character codes only (e.g., `BD`, not `BGD`) |

---

## Common Use Cases

### Use Case 1: Data Provenance and Verification

**Goal:** Understand all contributions made to a facility profile

```bash
GET /api/facilities/?q=Example+Factory&detail=true
```

**Why use this endpoint:** Only the Facilities endpoint provides complete contribution history and extended details showing what each contributor has added to a facility profile.

---

### Use Case 2: Contributor-Specific Data Analysis

**Goal:** Analyze facilities reported by a specific organization

```bash
GET /api/facilities/?contributors=123&detail=true
```

**Why use this endpoint:** Contributor filtering is unique to the Facilities endpoint. Production Locations does not support searching by contributor.

---

### Use Case 3: Supplier Discovery

**Goal:** Find apparel manufacturers in Bangladesh

```bash
GET /api/facilities/?sector=Apparel&countries=BD&pageSize=50
```

---

### Use Case 4: Multi-Contributor Verification

**Goal:** Find facilities verified by multiple data sources

```bash
GET /api/facilities/?contributors=123&contributors=456&combine_contributors=AND
```

**Why use this endpoint:** Only the Facilities endpoint supports contributor intersection queries to find facilities with data from multiple specific sources.

---

### Use Case 5: Parent Company Portfolio

**Goal:** Map all facilities owned by a corporation

```bash
GET /api/facilities/?parent_company=Nike
```

---

### Use Case 6: Processing Type Research

**Goal:** Identify all dyeing and printing facilities

```bash
GET /api/facilities/?processing_type=Dyeing&processing_type=Printing
```

---

## Facilities vs Production Locations Endpoints

### Use Facilities Endpoint When You Need:

| Capability | Facilities Endpoint | Production Locations Endpoint |
|------------|---------------------|-------------------------------|
| **View all contributions to a facility** | ✅ Yes (`detail=true`) | ❌ No |
| **See extended details & data provenance** | ✅ Yes | ❌ No |
| **Filter by contributor** | ✅ Yes | ❌ No |
| **Filter by contributor type** | ✅ Yes | ❌ No |
| **Contributor intersection queries** | ✅ Yes (`combine_contributors=AND`) | ❌ No |
| **Fuzzy search with typo tolerance** | ❌ No | ✅ Yes |
| **Geographic radius/bounding box search** | ❌ No | ✅ Yes |
| **Address-based search** | ❌ No | ✅ Yes |

### Key Differences

**Facilities Endpoint:**
- Exact matching only
- Supports contributor-based filtering and analysis
- **Only endpoint that shows complete contribution history**
- Best for understanding data provenance and attribution

**Production Locations Endpoint:**
- Fuzzy matching with typo tolerance
- Geographic search capabilities
- No contributor filtering
- No extended details
- Best for discovery and location-based search

---

## Error Handling

### Common Errors

| Error | Cause | Solution |
|-------|-------|----------|
| Invalid country code | Wrong format (e.g., `USA` instead of `US`) | Use two-character ISO codes from `/countries/` |
| Invalid contributor ID | Non-existent ID | Retrieve valid IDs from `/contributors/` |
| Page size too large | Exceeds limit | Use max 50 (detail=false) or 10 (detail=true) |

---

## Related Documentation

- [Production Locations Search (Fuzzy)](./production-locations-search.md)
- [GET Facility by OS ID](../reference/facilities-get-by-id.md)
- [POST Facility Data](../reference/facilities-post.md)
- [Reference Data Endpoints](../reference/)

---

## Support

Need help? Open an issue in our [GitHub repository](https://github.com/opensupplyhub) or contact the OS Hub team.
