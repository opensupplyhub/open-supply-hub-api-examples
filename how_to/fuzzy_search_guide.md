# Searching for Facilities on Open Supply Hub

The `GET /api/v1/production-locations/` endpoint provides intelligent search capabilities that help you find production locations even with incomplete information, typos, or partial addresses—similar to how Google search works.

## Quick Start

All searches use the base endpoint:

```
https://opensupplyhub.org/api/v1/production-locations/
```

**Key Feature:** All text searches (`name=`, `address=`, `query=`) use fuzzy matching, which means typos and variations are automatically handled.

---

## Search Methods

### By Name

Search specifically in the facility name field:

```
GET /api/v1/production-locations/?name=steinway+sons
```

**Best for:** When you know the company or facility name

[Try it →](https://opensupplyhub.org/api/v1/production-locations/?name=steinway+sons)

### By Address

Search specifically in the address field:

```
GET /api/v1/production-locations/?address=astoria
```

**Best for:** When you have city, state, or street information

[Try it →](https://opensupplyhub.org/api/v1/production-locations/?address=astoria)

### Combined Name + Address

Combine multiple parameters for precise results:

```
GET /api/v1/production-locations/?name=steinway&address=astoria
```

**Best for:** Maximum precision when you have both name and location

[Try it →](https://opensupplyhub.org/api/v1/production-locations/?name=steinway&address=astoria)

### General Query

Search across multiple fields (name, address, description, local name):

```
GET /api/v1/production-locations/?query=steinway+piano
```

**Best for:** Exploratory searches when you're not sure which field contains your information

[Try it →](https://opensupplyhub.org/api/v1/production-locations/?query=steinway+piano)

### Geographic Search

Find facilities within a radius of coordinates:

```
GET /api/v1/production-locations/?coordinates[lat]=40.7726&coordinates[lng]=-73.9076&distance=2km
```

**Best for:** Location-based discovery

[Try it →](https://opensupplyhub.org/api/v1/production-locations/?coordinates[lat]=40.7726&coordinates[lng]=-73.9076&distance=2km)

---

## Search Parameters

### Text Search (Fuzzy Matching Enabled)

| Parameter | Description | Example |
|-----------|-------------|---------|
| `query` | Multi-field search (name, address, description, local name) | `?query=textile+factory` |
| `name` | Facility name only | `?name=steinway` |
| `address` | Address only | `?address=new+york` |
| `description` | Description field only | `?description=apparel` |
| `local_name` | Local language name | `?local_name=工厂` |

### Filters (Exact Match)

| Parameter | Description | Example |
|-----------|-------------|---------|
| `country` | Two-letter country code | `?country=US` |
| `sector` | Industry sector | `?sector=Apparel` |
| `product_type` | Product type filter | `?product_type=shirts` |
| `processing_type` | Processing type | `?processing_type=dyeing` |
| `os_id` | Exact OS ID match | `?os_id=US2025026H5N0X1` |

### Geographic Search

| Parameter | Type | Description |
|-----------|------|-------------|
| `coordinates[lat]` | float | Latitude |
| `coordinates[lng]` | float | Longitude |
| `distance` | string | Radius (e.g., `50km`, `10mi`) |

### Range Filters

| Parameter | Type | Description |
|-----------|------|-------------|
| `number_of_workers[min]` | integer | Minimum worker count |
| `number_of_workers[max]` | integer | Maximum worker count |
| `percent_female_workers[min]` | float | Minimum percentage |
| `percent_female_workers[max]` | float | Maximum percentage |

### Pagination

| Parameter | Type | Description |
|-----------|------|-------------|
| `size` | integer | Results per page |
| `from` | integer | Offset for pagination |
| `search_after[value]` | string | Cursor value for deep pagination |
| `search_after[id]` | string | Cursor ID for deep pagination |

### Sorting

| Parameter | Values | Description |
|-----------|--------|-------------|
| `sort_by` | `name`, `address`, `claimed_at` | Field to sort by |
| `order_by` | `asc`, `desc` | Sort direction |

---

## Examples

### Example 1: Finding Steinway & Sons

Search by name:
```
GET /api/v1/production-locations/?name=steinway+sons
```
**Result:** 41 facilities with "Steinway" in the name

### Example 2: Typo Tolerance

Search with a typo:
```
GET /api/v1/production-locations/?name=stienway
```
**Result:** Still finds Steinway facilities (handles up to 2 character edits)

### Example 3: Precise Location Search

Combine name and location:
```
GET /api/v1/production-locations/?name=steinway&address=astoria
```
**Result:** 5 facilities - all Steinway locations in Astoria, NY

### Example 4: Country and Sector Filtering

Find apparel facilities in Bangladesh:
```
GET /api/v1/production-locations/?sector=Apparel&country=BD
```

### Example 5: Geographic Radius Search

Find all facilities within 50km of Dhaka:
```
GET /api/v1/production-locations/?coordinates[lat]=23.8103&coordinates[lng]=90.4125&distance=50km
```

---

## Understanding Fuzzy Matching

### How It Works

Fuzzy matching allows up to 2 character edits using Damerau-Levenshtein distance:

- **Insertion** - adding a character (`astria` → `astoria`)
- **Deletion** - removing a character (`steinwayy` → `steinway`)
- **Substitution** - replacing a character (`astria` → `austria`)
- **Transposition** - swapping adjacent characters (`stienway` → `steinway`)

### Which Parameters Use Fuzzy Matching?

✅ **Fuzzy Matching Enabled:**
- `query=`
- `name=`
- `address=`
- `description=`
- `local_name=`

❌ **Exact Match Only:**
- `country=`
- `sector=`
- `os_id=`
- Geographic parameters

### When Fuzzy Matching Can Be Too Broad

Searching for `address=astria` returns 5,694 results because it matches both:
- "Astoria" (1 edit: add 'o')
- "Austria" (1 edit: change 'i' to 'u')

**Solution:** Be more specific by adding additional parameters to narrow results.

---

## Best Practices

### When to Use Each Search Method

| Situation | Best Method | Example |
|-----------|-------------|---------|
| You know the company name | `name=` | `?name=steinway` |
| You have an address | `address=` | `?address=astoria` |
| You have name + location | Combined | `?name=steinway&address=astoria` |
| You're exploring | `query=` | `?query=piano+factory` |
| You have coordinates | Geographic | `?coordinates[lat]=40.77&coordinates[lng]=-73.91` |
| You have a partial OS ID | `os_id=` | `?os_id=US2025026H5N0X1` |

### Optimization Tips

**1. Use `name=` instead of `query=` when you know the company name**
- `name=steinway` → 41 results (focused)
- `query=steinway` → 95 results (broader)

**2. Add location to narrow results**
- `name=steinway` → 41 results
- `name=steinway&address=astoria` → 5 results

**3. All text searches tolerate typos**
```
name=stienway (typo) → Still finds Steinway ✓
address=astria (typo) → Still finds Astoria ✓
```

**4. Combine filters for precision**
```
?name=textile&country=BD&sector=Apparel
```

---

## Response Format

### Typical Response Structure

```json
{
  "count": 5,
  "next": null,
  "previous": null,
  "results": [
    {
      "os_id": "US2025026H5N0X1",
      "name": "Steinway & Sons - New York Factory",
      "address": "1 Steinway Place, Astoria, NY 11105, USA",
      "country_code": "US",
      "location": {
        "lat": 40.7726,
        "lng": -73.9076
      },
      "sector": ["Manufacturing"],
      "number_of_workers": 350,
      "created_at": "2024-01-15T10:30:00Z"
    }
  ]
}
```

---

## Advanced Features

### Query Adaptation

The system automatically adapts search behavior based on query length:

| Query Type | Condition | Search Method |
|------------|-----------|---------------|
| Short queries | < 12 words AND < 180 chars | Fuzzy matching (fuzziness: 2) |
| Long queries | ≥ 12 words OR ≥ 180 chars | Phrase matching (slop: 3) |

### Multi-Language Support

The search works with both English and local language names:
```
?query=工厂  # Searches local_name field
?local_name=São+Paulo  # Accent normalization applied
```

### Ranking

Results are ranked by relevance:
- Name matches receive 2× boost in `query=` searches
- Exact matches rank higher than fuzzy matches
- Multiple field matches increase score

---

## Geographic Search Options

### 1. Radius Search

Find facilities within a distance from a point:
```
?coordinates[lat]=40.7726&coordinates[lng]=-73.9076&distance=2km
```

### 2. Bounding Box

Define a rectangular area:
```
?geo_bounding_box[top]=40.8
&geo_bounding_box[left]=-74.0
&geo_bounding_box[bottom]=40.7
&geo_bounding_box[right]=-73.9
```

### 3. Custom Polygon

For complex geographic queries, use the web interface or API to define custom shapes.

---

## Performance

- **Response Time:** Sub-second, typically under 200ms
- **Accent Handling:** Automatic normalization (e.g., "São Paulo" matches "sao paulo")
- **Search Engine:** Powered by OpenSearch with custom analyzers

---

## Common Questions

**Q: How accurate is the fuzzy search?**  
Very accurate. The system uses accent normalization and allows up to 2 character edits, handling most common typos while maintaining precision.

**Q: Do I need to include accents in search terms?**  
No. The system automatically normalizes accents, so "São Paulo" and "sao paulo" both work.

**Q: Can I search by location on a map?**  
Yes! Use radius search, bounding box, or custom polygon options for geographic queries.

**Q: What happens if I paste a full address?**  
The system automatically detects long queries and switches to phrase-based matching, which is optimized for addresses.

**Q: How do I get more than the default number of results?**  
Use the `size` parameter: `?name=textile&size=100`

---

## Rate Limits

Please refer to the main API documentation for current rate limit information.

---

## Full API Documentation

For complete API reference including authentication, rate limits, and all endpoints:

📚 **[Open Supply Hub API Documentation](https://opensupplyhub.github.io/open-supply-hub-api-docs/)**

---

## Support

If you encounter issues or have questions:

1. Check the [full API documentation](https://opensupplyhub.github.io/open-supply-hub-api-docs/)
2. Review examples above
3. Contact support through the Open Supply Hub platform

---

## Contributing

We welcome contributions! If you find issues or have suggestions for improving this documentation, please open an issue or submit a pull request.
