# Searching for Facilities on Open Supply Hub using the /facilities/ endpoint

## Use the **Facilities endpoint** (`/api/facilities/`) when you need:

- ✅ **View all contributions to a facility** - See extended details showing every data contribution made to a facility profile
- ✅ **Search by contributor** - Filter facilities by specific contributor IDs or types
- ✅ **Contributor intersection queries** - Find facilities with data from multiple contributors
- ✅ **Parent company filtering** - Search by parent company ownership
- ✅ **Detailed attribution** - See complete contributor information and data provenance

> **📌 Looking for fuzzy search?** The `/api/facilities/` endpoint has limited fuzzy search support. For fuzzy search with typo tolerance, geographic search, or address-based search, use the [v1/production-locations/ endpoint](https://github.com/opensupplyhub/open-supply-hub-api-examples/blob/main/how_to/fuzzy_search_guide.md) instead. Note that this endpoint does not support extended details or contributor-based filtering.

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
| `combine_contributors` | string | `OR` | Set this to `AND` to return only the facilities with all specified contributors (overlap)  |
| `sort_by` | string | `contributors` | The results are sorted by most to least `contributors` by default. Set to `NAME` to sort alphabetically |
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
| `contributor_types` | string | **Filter by contributor type** (e.g., Brand, Multi-Stakeholder Initiative). Unique to Facilities endpoint. Get types from the GET /contributor-types/ endpoint|
| `parent_company` | string | Filter by parent company name or contributor ID. Get companies from the GET /parent-companies/ endpoint|
| `facility_type` | string | Filter by [facility type](https://docs.google.com/spreadsheets/d/18ABJuS5CY4cr9JaTzPeLaAr1uhdu7VJXK6JpibP1b1o/edit?gid=0#gid=0) (e.g., "Final Product Assembly")|
| `processing_type` | string | Filter by [processing type](https://docs.google.com/spreadsheets/d/18ABJuS5CY4cr9JaTzPeLaAr1uhdu7VJXK6JpibP1b1o/edit?gid=0#gid=0) (e.g., "Assembly", "Cutting") |

---

## Response Format

Responses are returned in **GeoJSON format** with the following structure:

### Basic Response (`detail=false`)

```json
{
    "type": "FeatureCollection",
    "count": 1,
    "next": null,
    "previous": null,
    "features": [
        {
            "id": "BD2021113R7R87P",
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [
                    90.418952,
                    23.896051
                ]
            },
            "properties": {
                "name": "Zaber & Zubair Fabrics Ltd",
                "address": "Pagar, Tongi, Gazipur Tongi, Gazipur Dhaka Gazipur 1710 Dhaka",
                "country_code": "BD",
                "os_id": "BD2021113R7R87P",
                "country_name": "Bangladesh",
                "has_approved_claim": true,
                "is_closed": null
            }
        }
    ],
    "extent": [
        90.41895199999999,
        23.896051,
        90.41895199999999,
        23.896051
    ],
    "params": {
        "contributors": [],
        "detail": false,
        "number_of_public_contributors": false,
        "sort_by": null,
        "embed": 0
    },
    "is_same_contributor": false
}
```

### Extended Response (`detail=true`)

**This is the only endpoint that provides complete contribution history for facilities.**

Additional fields included when `detail=true`:
- **Full facility profile** - All data points aggregated from multiple contributors, showing the complete picture of what's known about the facility
- **All contributor information** - See every organization that has contributed data for this facility, including Contributor ID and Contributor Name
- **List Names** - Additional context about each data submission (provided by the contributor when uploading, such as "Q3 2024 Supplier List" or "Authorized Manufacturer List")
- **Extended fields** - Complete list of all data attributes (product types, certifications, worker counts, etc.) with the contributor and date for each value


> **💡 Use Case:** When you need to understand what data each contributor has provided about a facility, or when you need to see the complete history of contributions, set `detail=true`. This is not available in the /v1/production-locations/ endpoint.

---

## Examples

### Example 1: Basic Text Search

Search for facilities with "textile" in the name:

```bash
GET /api/facilities/?q=textile
```

**Returns:** All facilities matching "textile" in the name

---

### Example 2: Country Filter

Find all facilities in Bangladesh:

```bash
GET /api/facilities/?countries=BD
```

**Returns:** All Bangladesh facilities

---

### Example 3: Combined Filters

Search for apparel facilities in Bangladesh:

```bash
GET /api/facilities/?sector=Apparel&countries=BD
```

---

### Example 4: View All Contributions to Facilities

Get complete contribution history for one facility with detailed attribution:

```bash
GET /api/facilities/?q=BD2021113R7R87P&detail=true
```

---

### Example 5: Specific Contributor Data

Find facilities uploaded by contributor ID 4302:

```bash
GET /api/facilities/?contributors=4302
```

**Returns:** Only facilities where contributor 4302 has submitted data

---

### Example 6: Multiple Contributors (Union)

Find facilities from contributor 4302 OR contributor 3617:

```bash
GET /api/facilities/?contributors=4302&contributors=3617
```

**Default behavior:** Returns facilities with data from either contributor

---

### Example 7: Multiple Contributors (Intersection)

Find facilities with data from BOTH contributors:

```bash
GET /api/facilities/?contributors=4302&contributors=3617&combine_contributors=AND
```

**Result:** Only facilities that have data from both contributor 4302 AND contributor 3617

> **Use Case:** Overlap analysis - find facilities that are connected with multiple contributors.

---

### Example 8: Filter by Contributor Type

Find facilities reported by brands specifically:

```bash
GET /api/facilities/?contributor_types=Brand
```

**Returns:** Facilities with data from brand contributors

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

## Best Practices

### 1. Use `detail=true` for Data Provenance

When you need to understand all contributions to a facility profile:

✅ **View complete contribution history:**
```bash
GET /api/facilities/?q=BD2021113R7R87P&detail=true
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

## Support

If you encounter issues or have questions:

1. Check the [full API documentation](https://github.com/opensupplyhub/open-supply-hub-api-examples)
2. Review examples above
3. [Contact support](support@opensupplyhub.org)

