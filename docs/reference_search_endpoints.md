# Quick Reference: Choosing Your Search Endpoint

## The Key Difference

**`/api/v1/production-locations/`** returns the **promoted data** for each facility—the same information displayed on the facility profile page, selected by OS Hub's promotion logic. Use this when you just want clean facility information for integrations or searches.

**`/api/facilities/`** returns **all contribution details** with the parameter detail=true, every data submission, historical changes, and contributor attribution. Use this for supply chain analysis, data provenance tracking, or understanding the full network of buyers and partners.

---

## 🎯 Quick Decision Guide

| **I want to...** | **Use This Endpoint** |
|------------------|----------------------|
| Get the promoted facility data (what's on the profile page) | `/api/v1/production-locations/` |
| Build a facility onboarding workflow or integration | `/api/v1/production-locations/` |
| Search with typos or partial addresses | `/api/v1/production-locations/` |
| Find facilities near coordinates | `/api/v1/production-locations/` |
| See all data contributions to a facility | `/api/facilities/` |
| Filter by specific contributors| `/api/facilities/` |
| Find facilitiy overlap between contributors | `/api/facilities/` |
| See who contributed which data points | `/api/facilities/` |

---

## 📊 Feature Comparison

| Feature | v1/production-locations/ | /facilities/ |
|---------|---------------------|-----------|
| **Data Returned** | Promoted data (profile page) | Promoted data and historical contributions |
| **Fuzzy Search** | ✅ | Limited |
| **Address Search** | ✅ | ❌ |
| **Geographic Search** | ✅ Radius & bounding box | ❌ |
| **Contributor Filtering** | ❌ | ✅ By Contributor ID |
| **Parent Company Search** | ❌ | ✅ |
| **Historical Data** | ❌ | ✅ Full contribution history |
| **Claim Search** | ✅ Status and time range| ❌ |

---

## 💡 Use Case Examples

### Example 1: Basic Integration
**Need:** Display facility information in your app.

```http
GET /api/v1/production-locations/?name=steinway&address=astoria
```
✅ **Production Locations** - Returns the promoted data without historical noise.

---

### Example 2: Supply Chain Network Analysis
**Need:** See which brands source from facility BD2021113R7R87P.

```http
GET /api/facilities/?q=BD2021113R7R87P&detail=true
```
✅ **Facilities** - Shows all contributors (buyers/partners) with full attribution.

---

### Example 3: Find all suppliers for a brand
**Need:** See all facilities that a specific brand sources from.

```http
GET /api/facilities/?contributors=4302&detail=true
```
✅ **Facilities** - Only this endpoint filters by contributor ID.

---

### Example 4: Geographic Search
**Need:** Find all facilities within 50km of Dhaka.

```http
GET /api/v1/production-locations/?coordinates[lat]=23.8103&coordinates[lng]=90.4125&distance=50km
```
✅ **Production Locations** - Only this endpoint supports coordinate search.

---

### Example 5: Supplier Overlap Analysis
**Need:** Find facilities shared between two brands.

```http
GET /api/facilities/?contributors=123&contributors=456&combine_contributors=AND
```
✅ **Facilities** - Identify facilities in multiple supply chains.

---

## 🔄 Using Both Endpoints Together

For optimal results, combine both endpoints in your workflow:

```bash
# Step 1: Fast search for facilities
GET /api/v1/production-locations/?name=textile&country=BD

# Step 2: Deep dive into specific facility's network
GET /api/facilities/?q=BD2021113R7R87P&detail=true
```

---

## 📚 Additional Resources

- [Guide: Searching for Facilities on Open Supply Hub using the /v1/production-locations/ endpoint](https://github.com/opensupplyhub/open-supply-hub-api-examples/blob/main/how_to/2_fuzzy_search_guide.md)
- [Guide: Searching for Facilities on Open Supply Hub using the /facilities/ endpoint](https://github.com/opensupplyhub/open-supply-hub-api-examples/blob/main/how_to/3_detail_search_guide.md))
- [Guide: Searching by Contributor](https://github.com/opensupplyhub/open-supply-hub-api-examples/blob/main/how_to/4_contributor-search-guide.md)
