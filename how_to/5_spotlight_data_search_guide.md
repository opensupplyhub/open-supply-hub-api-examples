# Accessing Spotlight Data via the OS Hub API

OS Hub Spotlight integrates data from a growing network of third-party partners, enabling you to retrieve environmental, social, and compliance data alongside core production location information. When Spotlight data exists for a location, it is included automatically in API responses — no additional parameters are required.

For more information about OS Hub Spotlight, see the [OS Hub Spotlight Page](https://info.opensupplyhub.org/spotlight), which covers:

- Active partners
- Available data points with definitions and additional resources
- How the data was sourced and how it can be used

> **Note:** Most production locations will only contain a subset of these fields. Spotlight data is only present when a partner has contributed information for that specific location. Do not expect every field to be populated in every response.

---

## Choosing an Endpoint

OS Hub provides two endpoints for retrieving a production location by OS ID:

| | Legacy Endpoint | New Endpoint |
|---|---|---|
| **Path** | `GET /api/facilities/{id}` | `GET /api/v1/production-locations/{os_id}` |
| **Endpoint reference** | [Legacy API Endpoints](https://opensupplyhub.org/api/docs/) | [NEW (Beta) API Endpoints](https://opensupplyhub.github.io/open-supply-hub-api-docs/) |
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
GET /api/facilities/BD2020021QK28YZ
```

### Example response structure

> **Note:** This is a real production location on OS Hub, so not all fields will be populated. For the complete schema including all possible fields, see the [Endpoint reference documentation](https://opensupplyhub.org/api/docs/).


```json
To be Updated Soon
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
GET /api/v1/production-locations/BD2020021QK28YZ
```

### Response structure

> **Note:** This is a real production location on OS Hub, so not all fields will be populated. For the complete schema including all possible fields, see the [Endpoint reference documentation](https://opensupplyhub.github.io/open-supply-hub-api-docs/).


```json
{
    "country": {
        "alpha_3": "BGD",
        "alpha_2": "BD",
        "name": "Bangladesh",
        "numeric": "050"
    },
    "parent_company": "Dekkoisho Group",
    "address": "Mawna, Sreepur, Gazipur-1740",
    "claim_status": "claimed",
    "certifications_standards_regulations": [
        "BCI",
        "FSC",
        "GOTS",
        "Global Recycling Standard (GRS)",
        "Higg Index",
        "Oeko-Tex Standard 100"
    ],
    "os_id": "BD2020021QK28YZ",
    "geocoded_location_type": "ROOFTOP",
    "coordinates": {
        "lat": 24.2206888,
        "lng": 90.41227169999999
    },
    "minimum_order_quantity": "25000",
    "affiliations": [
        "Better Work (ILO)",
        "Ethical Trading Initiative",
        "HERhealth",
        "SEDEX",
        "Social and Labor Convergence Plan (SLCP)"
    ],
    "description": "Facility is LEED Gold Certified Readymade Manufacturing Garments . Facility has GOTS,OCS,GRS,RCS,FSC,EUROPEAN FLAX, OEKOTEX certificates and member of BSCI, SEDEX,HIGG,SLCP,BETTERWORK & ICS. It's manufacturing process are Cutting, Embroidery, Sewing, Finishing, Packing, Export. \nMonthly Production Capacity 1.35 Million Units. Total Sewing lines 45. We are using Energy efficient motors for all Machineries. \nFacility has Rain Water Harvesting, Sewage Treatment Plant, Solar System, 30% Green Area.",
    "local_name": "Dekko Garments Ltd.",
    "location_type": [
        "Final Product Assembly",
        "Textile or Material Production",
        "Printing, Product Dyeing and Laundering"
    ],
    "percent_female_workers": 60,
    "claimed_at": "2026-04-04T06:17:21.227785Z",
    "product_type": [
        "All types of Woven Bottoms & Tops"
    ],
    "geocoded_address": "1740 Mawna - Sreepur Rd, Mawna Union, Bangladesh",
    "historical_os_id": [
        "BD2019086HB8VVT",
        "BD2024197QKS136"
    ],
    "name": "Dekko Garments Ltd.",
    "number_of_workers": {
        "min": 5300,
        "max": 5300
    },
    "business_url": "www.dekkoisho.com",
    "sector": [
        "Apparel"
    ],
    "processing_type": [
        "Cut & Sew",
        "Embroidery",
        "Final Product Assembly",
        "Finishing"
    ],
    "average_lead_time": "90-120 Days",
    "accord_inspections_and_remediation_program": {
        "rsc_presence": "Yes",
        "first_inspection_date": "2019-04-08"
    },
    "amfori_compliance_status": {
        "bsci_audit": {
            "expiration_date": "2026-11-21",
            "submission_date": "2024-11-21"
        },
        "environmental_risk_assessment": {
            "completion_date": "2026-01-22"
        },
        "bepi_audit": {}
    },
    "slcp_assessment": {
        "verifier_body": "N/A - Better Work Bangladesh (not a Verifier Body)",
        "slcp_facility_id": "FA500170",
        "assessment_platform": "N/A - Data shared by Better Work",
        "most_recent_assessment_date": "2026-03-30",
        "most_recent_assessment_status": "Assessment Initiated"
    },
    "wrap_certification": {
        "issue_date": "2025-05-12",
        "expiration_date": "2026-05-12",
        "certification_status": "active"
    },
    "climate_trace_emissions": {
        "emissions_model": "Fully Modeled",
        "estimated_emissions": 546
    },
    "rsc_grievance_mechanism": {
        "status": "Active",
        "internal_ID": "9214",
        "thematic_coverage": "Multi-issue",
        "mechanism_type_ownership": "Multi-stakeholder led",
        "access_modality": "Hotline; Email; In-person",
        "coverage": "All workers (factory-level)"
    }
```
## Frequently Asked Questions

**Will every production location have partner data?**

No. Partner data is only present when a partner has contributed information for that specific location. Most production locations will only contain a subset of partner data fields, so responses will vary.

**Can I retrieve partner data when searching across multiple production locations?**

No. Partner data is only returned when retrieving a specific production location by OS ID. It is not included in list responses, such as filtered searches by country, sector, or other parameters.

**How many API calls are needed to retrieve partner data for a production location?**

One. Partner data is included in the same response as the core production location data, so a single call per OS ID is all that is required.
