# Accessing Partner Data via the OS Hub API

Open Supply Hub (OS Hub) integrates data from a growing network of third-party partners, enabling you to retrieve environmental, social, and compliance data alongside core production location information. When partner data exists for a location, it is included automatically in API responses — no additional parameters are required.

For more information about OS Hub's data partnerships, see the [OS Hub Data Integrations page](https://info.opensupplyhub.org/data-integrations), which covers:

- Active partners
- Available data points with definitions and additional resources
- How the data was sourced and how it can be used

> **Note:** Most production locations will only contain a subset of these fields. Partner data is only present when a partner has contributed information for that specific location. Do not expect every field to be populated in every response.

---

## Choosing an Endpoint

OS Hub provides two endpoints for retrieving a production location by OS ID:

| | Legacy Endpoint | New Endpoint |
|---|---|---|
| **Path** | `GET /api/facilities/{id}` | `GET /api/v1/production-locations/{os_id}` |
| **Partner data location** | Nested under `properties.partner_fields` | Top-level fields |
| **Partner data structure** | Array of contribution objects with metadata (contributor name, verification status, timestamps) | Clean key-value pairs with raw values only |
| **Best for** | Accessing contributor metadata and provenance | Straightforward data integration |

---

## Legacy Endpoint

### Request

```
GET /api/facilities/{id}
```

**Example:**

```
GET /api/facilities/BD2019086FE689M
```

### Example response structure

The legacy endpoint returns a GeoJSON `Feature` object. Partner data is nested inside `properties.partner_fields` as an array of contribution objects. Each object includes contributor metadata alongside the raw values.

> **IMPORTANT:** The following response example illustrate what a fully populated production location may look like when data has been contributed by multiple partners. In practice, most production locations will only contain a subset of these fields, depending on whether partner data exists for that specific location. As a result, API responses will vary and should not be expected to include data from every partner for every production location.

```json
{
  "id": "BD2019086FE689M",
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [90.304338, 23.9431596]
  },
  "properties": {
    "name": "Debonair Limited",
    "address": "Gorat, Sarker Market Road, Ashulia",
    "country_code": "BD",
    "os_id": "BD2019086FE689M",
    "country_name": "Bangladesh",
    "partner_fields": {
      "wage_indicator": [
        {
          "id": null,
          "is_verified": false,
          "value": {
            "raw_values": {
              "living_wage_link_national": "https://mywage.org.bd/salary/living-wages",
              "minimum_wage_link_english": "https://wageindicator.org/salary/minimum-wage/bangladesh/38276-bangladesh",
              "minimum_wage_link_national": "https://mywage.org.bd/salary/minimum-wage/"
            }
          },
          "updated_at": "2026-01-17T07:30:43.699192Z",
          "contributor_name": "WageIndicator",
          "contributor_id": 2868,
          "value_count": 1,
          "is_from_claim": false,
          "field_name": "wage_indicator",
          "verified_count": 0
        }
      ],
      "climate_trace": [
        {
          "value": {
            "raw_values": {
              "estimated_emissions": 13,
              "estimated_annual_activity": 22
            }
          },
          "updated_at": "2026-03-01T09:15:00.000000Z",
          "contributor_name": "Climate TRACE",
          "contributor_id": 2950
        }
      ]
    }
  }
}
```

### Key metadata fields in `partner_fields`

| Field | Description |
|---|---|
| `value.raw_values` | The partner's contributed data |
| `contributor_name` | Name of the contributing partner organisation |
| `contributor_id` | Numeric ID of the contributor |
| `updated_at` | Timestamp of the most recent update |

---

## New Endpoint

### Request

```
GET /api/v1/production-locations/{os_id}
```

**Example:**

```
GET /api/v1/production-locations/BD2019086FE689M
```

### Response structure

The new endpoint returns a flat JSON object. Partner data appears as top-level fields, with raw values directly accessible — no unwrapping of contribution arrays is needed.

> **IMPORTANT:** The following response example illustrate what a fully populated production location may look like when data has been contributed by multiple partners. In practice, most production locations will only contain a subset of these fields, depending on whether partner data exists for that specific location. As a result, API responses will vary and should not be expected to include data from every partner for every production location.

```json
{
  "os_id": "BD2019086FE689M",
  "name": "Debonair Limited",
  "address": "Gorat, Sarker Market Road, Ashulia",
  "coordinates": {
    "lat": 23.9431596,
    "lng": 90.304338
  },
  "country": {
    "name": "Bangladesh",
    "alpha_2": "BD"
  },
  "sector": ["Apparel"],
  "claim_status": "claimed",
  "wage_indicator": {
    "living_wage_link_national": "https://mywage.org.bd/salary/living-wages",
    "minimum_wage_link_english": "https://wageindicator.org/salary/minimum-wage/bangladesh/38276-bangladesh",
    "minimum_wage_link_national": "https://mywage.org.bd/salary/minimum-wage/"
  },
  "amfori_compliance_status": {
    "bsci_audit": {
      "submission_date": "2024-10-15",
      "expiration_date": "2026-10-15"
    },
    "bepi_audit": {
      "submission_date": "2024-11-20",
      "expiration_date": "2026-11-20"
    },
    "environmental_risk_assessment": {
      "completion_date": "2024-12-01",
      "expiration_date": "2026-12-01"
    }
  },
  "estimated_emissions": 13,
  "estimated_annual_activity": 22,
  "worldly_assessment_data": {
    "fem_assessment": {
      "last_date": "2024-06-15T10:30:00Z",
      "verification_status": "verified",
      "reporting_year": 2024,
      "assessment_url": "https://worldly.io/assessments/fem/fem_2024_bd2019086fe689m"
    }
  },
  "ulula_grievance_mechanism": {
    "status": "active",
    "start_date": "2024-01-20"
  }
}
```
## Frequently Asked Questions

**Will every production location have partner data?**

No. Partner data is only present when a partner has contributed information for that specific location. Most production locations will only contain a subset of partner data fields, so responses will vary.

**Can I retrieve partner data when searching across multiple production locations?**

No. Partner data is only returned when retrieving a specific production location by OS ID. It is not included in list responses, such as filtered searches by country, sector, or other parameters.

**How many API calls are needed to retrieve partner data for a production location?**

One. Partner data is included in the same response as the core production location data, so a single call per OS ID is all that is required.
