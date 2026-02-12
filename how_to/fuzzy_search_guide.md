# Searching for Facilities on Open Supply Hub using the /v1/production-locations/ endpoint

The `GET /api/v1/production-locations/` endpoint provides intelligent search capabilities that help you find production locations even with incomplete information, typos, or partial addresses—similar to how Google search works.

## Quick Start

All searches use the base endpoint:

```
https://opensupplyhub.org/api/v1/production-locations/
```
Find related documentation [here](https://opensupplyhub.github.io/open-supply-hub-api-docs/)

**Key Feature:** All text searches (`name=`, `address=`, `query=`) use fuzzy matching, which means typos and variations are automatically handled.

---

## Search Methods

### By Name

Search specifically in the facility name field:

```
GET /api/v1/production-locations/?name=steinway+sons
```

**Best for:** When you know the company or facility name

### By Address

Search specifically in the address field:

```
GET /api/v1/production-locations/?address=astoria
```

**Best for:** When you have city, state, or street information

### Combined Name + Address

Combine multiple parameters for precise results:

```
GET /api/v1/production-locations/?name=steinway&address=astoria
```

**Best for:** Maximum precision when you have both name and location

### General Query

Search across multiple fields (name, address, description, local name):

```
GET /api/v1/production-locations/?query=steinway+piano
```

**Best for:** Exploratory searches when you're not sure which field contains your information

### Geographic Search

Find facilities within a radius of coordinates:

```
GET /api/v1/production-locations/?coordinates[lat]=13.0454318&coordinates[lng]=77.5218658&distance=2km
```

**Best for:** Location-based discovery

---

## Search Parameters

### Text Search (Fuzzy Matching Enabled)

| Parameter | Description | Example |
|-----------|-------------|---------|
| `query` | Multi-field search (name, address, description, local name) | `?query=textile+factory` |
| `name` | Facility name only | `?name=steinway` |
| `address` | Address only | `?address=new+york` |
| `description` | Description field only | `?description=apparel` |
| `local_name` | Local language name | `?local_name=温岭市名仕帽业有限公司` |

### Filters (Exact Match Only)

| Parameter | Description | Example |
|-----------|-------------|---------|
| `country` | Two-letter country code | `?country=US` |
| `sector` | [Industry sector](https://docs.google.com/document/d/12gDb4WlMHwaAE0iYVmbOjNJ_T7ICqntp-Ddd1qfbhCg/edit?tab=t.0#heading=h.tnf5hn3volep) | `?sector=Apparel` |
| `product_type` | [Product type](https://docs.google.com/spreadsheets/d/18ABJuS5CY4cr9JaTzPeLaAr1uhdu7VJXK6JpibP1b1o/edit?gid=0#gid=0) | `?product_type=shirts` |
| `processing_type` | [Processing type](https://docs.google.com/spreadsheets/d/18ABJuS5CY4cr9JaTzPeLaAr1uhdu7VJXK6JpibP1b1o/edit?gid=0#gid=0) | `?processing_type=dyeing` |
| `os_id` | Exact OS ID match | `?os_id=US2025026H5N0X1` |

### Geographic Search

| Parameter | Type | Description |
|-----------|------|-------------|
| `coordinates[lat]` | float | Latitude |
| `coordinates[lng]` | float | Longitude |
| `distance` | string | Radius (e.g., `50km`, `10mi`) |
| `geo_bounding_box[top]` | float | Bounding box top latitude |
| `geo_bounding_box[left]` | float | Bounding box left longitude |
| `geo_bounding_box[bottom]` | float | Bounding box bottom latitude |
| `geo_bounding_box[right]` | float | Bounding box right longitude |

### Range Filters

| Parameter | Type | Description |
|-----------|------|-------------|
| `number_of_workers[min]` | integer | Minimum worker count |
| `number_of_workers[max]` | integer | Maximum worker count |
| `percent_female_workers[min]` | float | Minimum percentage |
| `percent_female_workers[max]` | float | Maximum percentage |
| `claimed_at_gt` | date | Claimed after this date |
| `claimed_at_lt` | date | Claimed before this date |

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

## Common Questions

**Q: How accurate is the fuzzy search?**  
Very accurate. The system uses accent normalization and allows up to 2 character edits, handling most common typos while maintaining precision.

**Q: Do I need to include accents in search terms?**  
No. The system automatically normalizes accents, so "São Paulo" and "sao paulo" both work.

**Q: Can I search by location on a map?**  
Yes! Use radius search, bounding box, or custom polygon options for geographic queries.

**Q: What happens if I paste a full address?**  
The system automatically detects long queries and switches to phrase-based matching, which is optimized for addresses.

---

## Rate Limits

Please refer to the main API documentation for current rate limit information [Link](https://github.com/opensupplyhub/open-supply-hub-api-examples/blob/main/docs/limitations.md).

---

## Full API Documentation

For complete API reference to all Beta endpoints:

📚 **[Open Supply Hub API Documentation](https://opensupplyhub.github.io/open-supply-hub-api-docs/)**

---

## Support

If you encounter issues or have questions:

1. Check the [full API documentation](https://github.com/opensupplyhub/open-supply-hub-api-examples)
2. Review examples above
3. [Contact support](support@opensupplyhub.org)

---

## Contributing

We welcome contributions! If you find issues or have suggestions for improving this documentation, please open an issue or submit a pull request.
