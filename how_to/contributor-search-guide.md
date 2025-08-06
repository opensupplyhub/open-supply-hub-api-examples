# Retrieving Contributor Data

## Use Case: Research and Supply Chain Analysis

This process is typically used by **researchers or civil society organizations who want to understand supply chain links** and relationships between brands, retailers, and suppliers. Researchers often want to download **all contributors** along with the lists they have uploaded and the associated facilities.

By following the steps below, researchers can systematically retrieve contributor data, their submitted lists, and the corresponding facilities.

## Instructions

### Step 1: Retrieve All Active Contributors

To get a list of all active contributors, use the `GET /api/contributors/` endpoint.

Each contributor in the response is identified by a **Contributor ID**.

**Sample response:**
```json
[
  [1632, "3FREUNDE", "Brand / Retailer"],
  [3404, "3F Tekstil Sanayi ve Dış Ticaret A.Ş.", "Facility / Factory / Manufacturing Group / Supplier / Vendor"],
  [9565, "4C (The Common Code for the Coffee Community) [Public List]", "Facility / Factory / Manufacturing Group / Supplier / Vendor"],
  [8432, "4imprint", "Facility / Factory / Manufacturing Group / Supplier / Vendor"]
]
```

### Step 2: Retrieve Lists Uploaded by a Contributor (Optional)

Once you have the **Contributor ID**, use the `GET /api/contributor-lists-sorted/` endpoint, filtering by the Contributor ID (`contributors` parameter).

This will return all active **lists** associated with that contributor, along with their **List IDs**.

NOTE: this step is optional and it's necessary only if you want to see the data organized by list. Otherwise, you can go to Step 3.

**Sample response (Contributor ID = 310):**
```json
[
  {
    "id": 4434,
    "name": "Zeeman tier 3 - Cotton suppliers (spinning - ginning - raw material processing) (April 2024)"
  },
  {
    "id": 4433,
    "name": "Zeeman tier 2 - Wet processing facilities (April 2024)"
  },
  {
    "id": 4432,
    "name": "Zeeman tier 1 - Direct suppliers (April 2024)"
  }
]
```

### Step 3: Retrieve Facilities Associated with Each List or with Each Contributor

To get all facilities contributed under a specific list, use `GET /api/facilities/` and filter by the **List ID** obtained in Step 2 (`lists` parameter).

To get all facilities contributed by a specific contributor, use `GET /api/facilities/` and filter by the **Contributor ID** obtained in Step 2 (`contributors` parameter).

**Sample response (List ID = 4434):**
```json
{
  "type": "FeatureCollection",
  "count": 297,
  "next": "https://opensupplyhub.org/api/facilities/?lists=4434&page=2",
  "previous": null,
  "features": [
    {
      "id": "PK2023025D2C48G",
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [67.2118619, 24.8555677]
      },
      "properties": {
        "name": "Gul Ahmed Textile Mills Ltd.",
        "address": "Plot No. H T-3/ A, H T-4, H T-7, H T-8, Landhi Industrial Area Karachi and Plot No. 82, 368, 369, Main National Highway, Landhi,",
        "country_code": "PK",
        "os_id": "PK2023025D2C48G",
        "country_name": "Pakistan",
        "has_approved_claim": false,
        "is_closed": null
      }
    }
  ]
}
```

---

## API Endpoints Summary

| Step | Method | Endpoint | Parameters | Purpose |
|------|--------|----------|------------|---------|
| 1 | `GET` | `/api/contributors/` | None | Retrieve all active contributors |
| 2 | `GET` | `/api/contributor-lists-sorted/` | `contributors` (Contributor ID) | Get lists uploaded by a contributor |
| 3 | `GET` | `/api/facilities/` | `lists` (List ID) | Get facilities associated with a list |
