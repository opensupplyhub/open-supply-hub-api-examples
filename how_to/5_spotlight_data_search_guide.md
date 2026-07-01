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
{
    "id": "BD2020021QK28YZ",
    "type": "Feature",
    "geometry": {
        "type": "Point",
        "coordinates": [
            90.394234,
            24.253563
        ]
    },
    "properties": {
        "name": "Dekko Garments Ltd.",
        "address": "Mawna, Sreepur, Gazipur-1740",
        "country_code": "BD",
        "os_id": "BD2020021QK28YZ",
        "other_names": [
            "DEKKO GARMENTS LTD",
            "Dekko Garments Ltd",
            "DEKKO GARMENTS LTD.",
            "Dekko Garments Limited",
            "DEKKO GARMENTS LIMITED"
        ],
        "other_addresses": [
            "MAWNA, SREEPUR, GAZIPUR,MAWNA UTTARPARA,,GAZIPUR, DHAKA,BANGLADESH",
            "Dekko Garments Ltd, Mawna, Sreepur\nDhaka zila\nGazipur\n1740",
            "Mawna,Sreepur,, Gazipur.",
            "Mawna, Sreepur, Gazipur   ",
            "MAWNA, SREEPUR, GAZIPUR, MAWNA UTTARPARA, GAZIPUR, DHAKA",
            "Nayanpur, Mawna, Sreepur BD, GAZIPUR SADAR, Bangladesh",
            "Mawna, Sreepur",
            "Mawna, Sreepur, Gazipur-1740.",
            "Mawna, Sreepur, 1740, Gazipur",
            "Nayanpur, Mawna, Sreepur, Gazipur.",
            "Mawna, Sreepur, Gazipur",
            "MAWNA, SREEPUR, GAZIPUR, Dhaka",
            "Mawna, Sreepur, Gazipur. Bangladesh",
            "Nayanpur, Mawna, Sreepur, Gazipur, Mawna Uttarpara, Gazipur 1703, Dhaka",
            "Mawna - Sreepur Rd, Sreepur, Bangladesh",
            "Mawna, Sreepur, Gazipur-1740",
            "Noyanpur Bazar Road, Mawna Union, Bangladesh",
            "Nayanpur, Mawna, Sreepur",
            "Mawna, Sreepur, Gazipur, Dhaka, Bangladesh",
            "Nayanpur, Mawna, Sreepur, Gazipur., Gazipur",
            "Mawna, Sreepur, Gazipur - 1740, Bangladesh",
            "Mawna, Sreepur, Gazipur, Nayanpur, Sreepur, Gazipur, GazipurBangladesh",
            "Mawna, Sreepur, Dhaka Gazipur 1703",
            "Mawna, Sreepur, Gazipur, Gazipur, Gazipur 1740",
            "Mawna, Sreepur, Gazipur, Gazipur, Gazipur, 1740",
            "MAWNA, SREEPUR,, GAZIPUR, Dhaka 1740",
            "Mawna, Sreepur, Gazipur.",
            "Mawna, 1740, Sreepur, Gazipur, Gazipur",
            "(Ground Floor), Dekko Garments Road, Nayanpur, Sreepur, Gazipur-1740",
            "Nayanpur, Mawna, Sreepur, 1703, Gazipur",
            "Mawna, Sreepur,Dhaka Gazipur",
            "Mawna, Sreepur, Gazipur, Dhaka",
            "Nayanpur, Mawna, Sreepur, 1740 Gazipur, Bangladesh"
        ],
        "contributors": [
            {
                "id": 26,
                "name": "Levi Strauss & Co. (Levi Strauss & Co. Direct Sourcing Factory List Q2 2026)",
                "is_verified": false,
                "contributor_name": "Levi Strauss & Co.",
                "contributor_type": "Brand / Retailer",
                "list_name": "Levi Strauss & Co. Direct Sourcing Factory List Q2 2026",
                "count": 1
            },
            {
                "id": 97,
                "name": "Fair Factories Clearinghouse (FFC Factory List Oct 2022)",
                "is_verified": false,
                "contributor_name": "Fair Factories Clearinghouse",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": "FFC Factory List Oct 2022",
                "count": 1
            },
            {
                "id": 205,
                "name": "Mapped in Bangladesh (MiB) - BRAC University (Mapped in Bangladesh Export Oriented RMG factory List, Bangladesh June 2025)",
                "is_verified": false,
                "contributor_name": "Mapped in Bangladesh (MiB) - BRAC University",
                "contributor_type": "Academic / Researcher / Journalist / Student",
                "list_name": "Mapped in Bangladesh Export Oriented RMG factory List, Bangladesh June 2025",
                "count": 1
            },
            {
                "id": 686,
                "name": "Worldly",
                "is_verified": false,
                "contributor_name": "Worldly",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": null,
                "count": 1
            },
            {
                "id": 841,
                "name": "HEMA B.V. (HEMA's Production Locations March 2022 - October 2022)",
                "is_verified": false,
                "contributor_name": "HEMA B.V.",
                "contributor_type": "Brand / Retailer",
                "list_name": "HEMA's Production Locations March 2022 - October 2022",
                "count": 1
            },
            {
                "id": 841,
                "name": "HEMA B.V. (HEMA Producion locations October 2023)",
                "is_verified": false,
                "contributor_name": "HEMA B.V.",
                "contributor_type": "Brand / Retailer",
                "list_name": "HEMA Producion locations October 2023",
                "count": 1
            },
            {
                "id": 841,
                "name": "HEMA B.V. (HEMA Facility List November 2024)",
                "is_verified": false,
                "contributor_name": "HEMA B.V.",
                "contributor_type": "Brand / Retailer",
                "list_name": "HEMA Facility List November 2024",
                "count": 1
            },
            {
                "id": 1050,
                "name": "ZDHC Foundation",
                "is_verified": false,
                "contributor_name": "ZDHC Foundation",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": null,
                "count": 1
            },
            {
                "id": 1237,
                "name": "Tom Tailor GmbH (Tom Tailor Facility List September 2021 Tier 1)",
                "is_verified": false,
                "contributor_name": "Tom Tailor GmbH",
                "contributor_type": "Brand / Retailer",
                "list_name": "Tom Tailor Facility List September 2021 Tier 1",
                "count": 1
            },
            {
                "id": 1237,
                "name": "Tom Tailor GmbH (Tom Tailor Tier 1 Facility List Mar 2023)",
                "is_verified": false,
                "contributor_name": "Tom Tailor GmbH",
                "contributor_type": "Brand / Retailer",
                "list_name": "Tom Tailor Tier 1 Facility List Mar 2023",
                "count": 1
            },
            {
                "id": 1237,
                "name": "Tom Tailor GmbH (Tom Tailor Tier 1 Facility List Mar 2024)",
                "is_verified": false,
                "contributor_name": "Tom Tailor GmbH",
                "contributor_type": "Brand / Retailer",
                "list_name": "Tom Tailor Tier 1 Facility List Mar 2024",
                "count": 1
            },
            {
                "id": 1342,
                "name": "Ralph Lauren Corporation (Supplier Disclosure T1 Factory 2023)",
                "is_verified": false,
                "contributor_name": "Ralph Lauren Corporation",
                "contributor_type": "Brand / Retailer",
                "list_name": "Supplier Disclosure T1 Factory 2023",
                "count": 1
            },
            {
                "id": 1342,
                "name": "Ralph Lauren Corporation (Supplier Disclosure T1 Factory 2 2026)",
                "is_verified": false,
                "contributor_name": "Ralph Lauren Corporation",
                "contributor_type": "Brand / Retailer",
                "list_name": "Supplier Disclosure T1 Factory 2 2026",
                "count": 1
            },
            {
                "id": 1673,
                "name": "KIABI (Kiabi Feb 5, 2025)",
                "is_verified": false,
                "contributor_name": "KIABI",
                "contributor_type": "Brand / Retailer",
                "list_name": "Kiabi Feb 5, 2025",
                "count": 1
            },
            {
                "id": 1673,
                "name": "KIABI (Kiabi Oct 6, 2025)",
                "is_verified": false,
                "contributor_name": "KIABI",
                "contributor_type": "Brand / Retailer",
                "list_name": "Kiabi Oct 6, 2025",
                "count": 1
            },
            {
                "id": 1673,
                "name": "KIABI (Kiabi Mar 6, 2026)",
                "is_verified": false,
                "contributor_name": "KIABI",
                "contributor_type": "Brand / Retailer",
                "list_name": "Kiabi Mar 6, 2026",
                "count": 1
            },
            {
                "id": 2144,
                "name": "Nirapon Inc. (Nirapon Factory list September 2025)",
                "is_verified": false,
                "contributor_name": "Nirapon Inc.",
                "contributor_type": "Civil Society Organization",
                "list_name": "Nirapon Factory list September 2025",
                "count": 1
            },
            {
                "id": 2144,
                "name": "Nirapon Inc. (Nirapon Factory List March 2026)",
                "is_verified": false,
                "contributor_name": "Nirapon Inc.",
                "contributor_type": "Civil Society Organization",
                "list_name": "Nirapon Factory List March 2026",
                "count": 1
            },
            {
                "id": 2238,
                "name": "International Accord",
                "is_verified": false,
                "contributor_name": "International Accord",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": null,
                "count": 1
            },
            {
                "id": 2238,
                "name": "International Accord (International Accord signatory Covered supplier list for Bangladesh May 2024)",
                "is_verified": false,
                "contributor_name": "International Accord",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": "International Accord signatory Covered supplier list for Bangladesh May 2024",
                "count": 1
            },
            {
                "id": 2238,
                "name": "International Accord (International Accord Signatory Covered Supplier List for Bangladesh October 2025)",
                "is_verified": false,
                "contributor_name": "International Accord",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": "International Accord Signatory Covered Supplier List for Bangladesh October 2025",
                "count": 1
            },
            {
                "id": 2238,
                "name": "International Accord (International Accord Signatory Covered Supplier List for Bangladesh March 2026)",
                "is_verified": false,
                "contributor_name": "International Accord",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": "International Accord Signatory Covered Supplier List for Bangladesh March 2026",
                "count": 1
            },
            {
                "id": 2238,
                "name": "International Accord (International Accord Signatory Covered Supplier List for Bangladesh June 2026)",
                "is_verified": false,
                "contributor_name": "International Accord",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": "International Accord Signatory Covered Supplier List for Bangladesh June 2026",
                "count": 1
            },
            {
                "id": 2745,
                "name": "BESTSELLER (Tier 1 and Tier 0 April 2026)",
                "is_verified": false,
                "contributor_name": "BESTSELLER",
                "contributor_type": "Brand / Retailer",
                "list_name": "Tier 1 and Tier 0 April 2026",
                "count": 1
            },
            {
                "id": 3126,
                "name": "Esprit (Esprit Facility List March 2023)",
                "is_verified": false,
                "contributor_name": "Esprit",
                "contributor_type": "Brand / Retailer",
                "list_name": "Esprit Facility List March 2023",
                "count": 1
            },
            {
                "id": 3365,
                "name": "amfori",
                "is_verified": false,
                "contributor_name": "amfori",
                "contributor_type": "Other",
                "list_name": null,
                "count": 1
            },
            {
                "id": 3394,
                "name": "Kontoor Brands, Inc. (KTB) (Kontoor Brands Inc. KTB Factory List valid on the date of publication 10.02.2025)",
                "is_verified": false,
                "contributor_name": "Kontoor Brands, Inc. (KTB)",
                "contributor_type": "Brand / Retailer",
                "list_name": "Kontoor Brands Inc. KTB Factory List valid on the date of publication 10.02.2025",
                "count": 1
            },
            {
                "id": 3394,
                "name": "Kontoor Brands, Inc. (KTB) (Kontoor Brands Inc. KTB Factory List valid on the date of publication 24 04 2025)",
                "is_verified": false,
                "contributor_name": "Kontoor Brands, Inc. (KTB)",
                "contributor_type": "Brand / Retailer",
                "list_name": "Kontoor Brands Inc. KTB Factory List valid on the date of publication 24 04 2025",
                "count": 1
            },
            {
                "id": 3757,
                "name": "Bangladesh Industrial Import Registration Certificate (IRC) [Public List] (Bangladesh Industrial IRC Facility List August 2022)",
                "is_verified": false,
                "contributor_name": "Bangladesh Industrial Import Registration Certificate (IRC) [Public List]",
                "contributor_type": "Auditor / Certification Scheme / Service Provider",
                "list_name": "Bangladesh Industrial IRC Facility List August 2022",
                "count": 1
            },
            {
                "id": 4402,
                "name": "Dekko Garments Ltd. (Dekko Garments Ltd.)",
                "is_verified": false,
                "contributor_name": "Dekko Garments Ltd.",
                "contributor_type": "Facility / Factory / Manufacturing Group / Supplier / Vendor",
                "list_name": "Dekko Garments Ltd.",
                "count": 1
            },
            {
                "id": 4699,
                "name": "J.Crew Group (J. Crew group factory list June 22 2026)",
                "is_verified": false,
                "contributor_name": "J.Crew Group",
                "contributor_type": "Brand / Retailer",
                "list_name": "J. Crew group factory list June 22 2026",
                "count": 1
            },
            {
                "id": 5102,
                "name": "Better Cotton (Better Cotton Initiative May 2021)",
                "is_verified": false,
                "contributor_name": "Better Cotton",
                "contributor_type": "Civil Society Organization",
                "list_name": "Better Cotton Initiative May 2021",
                "count": 1
            },
            {
                "id": 6294,
                "name": "PVH (PVH Brand Facility List Dec 2022)",
                "is_verified": false,
                "contributor_name": "PVH",
                "contributor_type": "Brand / Retailer",
                "list_name": "PVH Brand Facility List Dec 2022",
                "count": 1
            },
            {
                "id": 6294,
                "name": "PVH (PVH Facility List June 2023)",
                "is_verified": false,
                "contributor_name": "PVH",
                "contributor_type": "Brand / Retailer",
                "list_name": "PVH Facility List June 2023",
                "count": 1
            },
            {
                "id": 6294,
                "name": "PVH (PVH Supplier List February 2026)",
                "is_verified": false,
                "contributor_name": "PVH",
                "contributor_type": "Brand / Retailer",
                "list_name": "PVH Supplier List February 2026",
                "count": 1
            },
            {
                "id": 6563,
                "name": "Sainsbury's (Sainsbury's Tier 1 GM and Clothing 2025)",
                "is_verified": false,
                "contributor_name": "Sainsbury's",
                "contributor_type": "Brand / Retailer",
                "list_name": "Sainsbury's Tier 1 GM and Clothing 2025",
                "count": 1
            },
            {
                "id": 6597,
                "name": "Dekko ISHO [Public List] (Dekko ISHO Group July 2024 Facility List)",
                "is_verified": false,
                "contributor_name": "Dekko ISHO [Public List]",
                "contributor_type": "Facility / Factory / Manufacturing Group / Supplier / Vendor",
                "list_name": "Dekko ISHO Group July 2024 Facility List",
                "count": 1
            },
            {
                "id": 7745,
                "name": "RISE (RISE HERhealth 2021 Completed)",
                "is_verified": false,
                "contributor_name": "RISE",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": "RISE HERhealth 2021 Completed",
                "count": 1
            },
            {
                "id": 8742,
                "name": "Target Corporation (Target Factory List February 2026)",
                "is_verified": false,
                "contributor_name": "Target Corporation",
                "contributor_type": "Brand / Retailer",
                "list_name": "Target Factory List February 2026",
                "count": 1
            },
            {
                "id": 11651,
                "name": "Wm Morrison Supermarkets Limited (Nutmeg T1 Facility List - July 2025)",
                "is_verified": false,
                "contributor_name": "Wm Morrison Supermarkets Limited",
                "contributor_type": "Brand / Retailer",
                "list_name": "Nutmeg T1 Facility List - July 2025",
                "count": 1
            },
            {
                "id": 11889,
                "name": "Worldwide Responsible Accredited Production (WRAP)",
                "is_verified": false,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "contributor_type": "Auditor / Certification Scheme / Service Provider",
                "list_name": null,
                "count": 1
            },
            {
                "id": 11889,
                "name": "Worldwide Responsible Accredited Production (WRAP) (WRAP Facility List December 2024)",
                "is_verified": false,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "contributor_type": "Auditor / Certification Scheme / Service Provider",
                "list_name": "WRAP Facility List December 2024",
                "count": 1
            },
            {
                "id": 11889,
                "name": "Worldwide Responsible Accredited Production (WRAP) (WRAP Facility List 04222025)",
                "is_verified": false,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "contributor_type": "Auditor / Certification Scheme / Service Provider",
                "list_name": "WRAP Facility List 04222025",
                "count": 1
            },
            {
                "id": 11889,
                "name": "Worldwide Responsible Accredited Production (WRAP) (WRAP's Facility List April 2026)",
                "is_verified": false,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "contributor_type": "Auditor / Certification Scheme / Service Provider",
                "list_name": "WRAP's Facility List April 2026",
                "count": 1
            },
            {
                "id": 12108,
                "name": "VARNER AS (Varner Facility List July 2023)",
                "is_verified": false,
                "contributor_name": "VARNER AS",
                "contributor_type": "Brand / Retailer",
                "list_name": "Varner Facility List July 2023",
                "count": 1
            },
            {
                "id": 12108,
                "name": "VARNER AS (Varner Factory List December 2024)",
                "is_verified": false,
                "contributor_name": "VARNER AS",
                "contributor_type": "Brand / Retailer",
                "list_name": "Varner Factory List December 2024",
                "count": 1
            },
            {
                "id": 12108,
                "name": "VARNER AS (Varner Factory List November 2025)",
                "is_verified": false,
                "contributor_name": "VARNER AS",
                "contributor_type": "Brand / Retailer",
                "list_name": "Varner Factory List November 2025",
                "count": 1
            },
            {
                "id": 12266,
                "name": "Tesco Stores Ltd (Home & Clothing Supply Chain List - August 2025)",
                "is_verified": false,
                "contributor_name": "Tesco Stores Ltd",
                "contributor_type": "Brand / Retailer",
                "list_name": "Home & Clothing Supply Chain List - August 2025",
                "count": 1
            },
            {
                "id": 13389,
                "name": "Social & Labor Convergence Program (SLCP)",
                "is_verified": false,
                "contributor_name": "Social & Labor Convergence Program (SLCP)",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": null,
                "count": 1
            },
            {
                "id": 13389,
                "name": "Social & Labor Convergence Program (SLCP) (Social & Labor Convergence Program List 2025)",
                "is_verified": false,
                "contributor_name": "Social & Labor Convergence Program (SLCP)",
                "contributor_type": "Multi-Stakeholder Initiative",
                "list_name": "Social & Labor Convergence Program List 2025",
                "count": 1
            },
            {
                "id": 17853,
                "name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                "is_verified": false,
                "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                "contributor_type": "Other",
                "list_name": null,
                "count": 1
            },
            {
                "id": 19188,
                "name": "Helly Hansen (Helly Hansen Tier 1 Facility List 2026)",
                "is_verified": false,
                "contributor_name": "Helly Hansen",
                "contributor_type": "Brand / Retailer",
                "list_name": "Helly Hansen Tier 1 Facility List 2026",
                "count": 1
            },
            {
                "id": 20593,
                "name": "Climate TRACE",
                "is_verified": false,
                "contributor_name": "Climate TRACE",
                "contributor_type": "Other",
                "list_name": null,
                "count": 1
            },
            {
                "name": "An Auditor / Certification Scheme / Service Provider",
                "contributor_type": "Auditor / Certification Scheme / Service Provider",
                "count": 1
            },
            {
                "name": "18 Brands / Retailers",
                "contributor_type": "Brand / Retailer",
                "count": 18
            },
            {
                "name": "2 Civil Society Organizations",
                "contributor_type": "Civil Society Organization",
                "count": 2
            },
            {
                "name": "4 Multi-Stakeholder Initiatives",
                "contributor_type": "Multi-Stakeholder Initiative",
                "count": 4
            }
        ],
        "country_name": "Bangladesh",
        "claim_info": {
            "id": 547,
            "office": {
                "name": "Dekko Garments Ltd.",
                "address": "Mawna, Sreepur, Gazipur-1740",
                "country": "BD",
                "phone_number": "01841297256"
            },
            "contact": {
                "name": "Arif Hasan Jony",
                "email": "arif.dgl@dekkoisho.com"
            },
            "facility": {
                "sector": [
                    "Apparel"
                ],
                "address": "Mawna, Sreepur, Gazipur-1740",
                "website": "www.dekkoisho.com",
                "location": {
                    "type": "Point",
                    "coordinates": [
                        90.4122717,
                        24.2206888
                    ]
                },
                "description": "Facility is LEED Gold Certified Readymade Manufacturing Garments . Facility has GOTS,OCS,GRS,RCS,FSC,EUROPEAN FLAX, OEKOTEX certificates and member of BSCI, SEDEX,HIGG,SLCP,BETTERWORK & ICS. It's manufacturing process are Cutting, Embroidery, Sewing, Finishing, Packing, Export. \nMonthly Production Capacity 1.35 Million Units. Total Sewing lines 45. We are using Energy efficient motors for all Machineries. \nFacility has Rain Water Harvesting, Sewage Treatment Plant, Solar System, 30% Green Area.",
                "affiliations": [
                    "Better Work (ILO)",
                    "Ethical Trading Initiative",
                    "HERhealth",
                    "SEDEX",
                    "Social and Labor Convergence Plan (SLCP)"
                ],
                "closing_date": null,
                "name_english": "Dekko Garments Ltd.",
                "opening_date": null,
                "phone_number": null,
                "facility_type": "Final Product Assembly|Textile or Material Production|Printing, Product Dyeing and Laundering",
                "minimum_order": "25000",
                "product_types": [
                    "All types of Woven Bottoms & Tops"
                ],
                "workers_count": "5300",
                "certifications": [
                    "BCI",
                    "FSC",
                    "GOTS",
                    "Global Recycling Standard (GRS)",
                    "Higg Index",
                    "Oeko-Tex Standard 100"
                ],
                "parent_company": {
                    "id": "Dekkoisho Group",
                    "name": "Dekkoisho Group"
                },
                "production_types": [
                    "Cut & Sew",
                    "Embroidery",
                    "Final Product Assembly",
                    "Finishing"
                ],
                "average_lead_time": "90-120 Days",
                "other_facility_type": null,
                "name_native_language": "Dekko Garments Ltd.",
                "female_workers_percentage": 60,
                "estimated_annual_throughput": null,
                "actual_annual_energy_consumption": {
                    "coal": null,
                    "other": null,
                    "diesel": null,
                    "biomass": null,
                    "charcoal": null,
                    "kerosene": null,
                    "electricity": null,
                    "natural_gas": null,
                    "animal_waste": null
                }
            },
            "created_at": "2023-01-24T03:03:31.688963+00:00",
            "contributor": "Dekko Garments Ltd.",
            "user_id": 4402
        },
        "other_locations": [
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 4402,
                "contributor_name": "Dekko Garments Ltd.",
                "notes": null,
                "is_from_claim": true,
                "has_invalid_location": false
            },
            {
                "lat": 24.2542614,
                "lng": 90.3941328,
                "contributor_id": null,
                "contributor_name": null,
                "notes": ""
            },
            {
                "lat": 24.253563,
                "lng": 90.394234,
                "contributor_id": 4402,
                "contributor_name": "Dekko Garments Ltd.",
                "notes": "https://plus.codes/7MPG793V+CMH\n\nhttps://www.google.com/maps/place/Dekko+Garments/@24.2151903,90.3074439,11z/data=!4m10!1m2!2m1!1sDekko+Garments,+Mawna,+Sreepur,+Gazipur-1740+-+Bangladesh!3m6!1s0x37567147a765ed6d:0x95d3e7c44bdb4f07!8m2!3d24.2535719!4d90.3942508!15sCjlEZWtrbyBHYXJtZW50cywgTWF3bmEsIFNyZWVwdXIsIEdhemlwdXItMTc0MCAtIEJhbmdsYWRlc2iSAR9jbG90aGVzX2FuZF9mYWJyaWNfbWFudWZhY3R1cmVy4AEA!16s%2Fg%2F11c2r5bj83?entry=ttu"
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 3394,
                "contributor_name": "Kontoor Brands, Inc. (KTB)",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 11651,
                "contributor_name": "Wm Morrison Supermarkets Limited",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 2144,
                "contributor_name": "Nirapon Inc.",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 1673,
                "contributor_name": "KIABI",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 17853,
                "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                "notes": null
            },
            {
                "lat": 23.9905079,
                "lng": 90.3877184,
                "contributor_id": 6563,
                "contributor_name": "Sainsbury's",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 12108,
                "contributor_name": "VARNER AS",
                "notes": null
            },
            {
                "lat": 24.2592925,
                "lng": 90.3983004,
                "contributor_id": 2238,
                "contributor_name": "International Accord",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 1673,
                "contributor_name": "KIABI",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 3365,
                "contributor_name": "amfori",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 12266,
                "contributor_name": "Tesco Stores Ltd",
                "notes": null
            },
            {
                "lat": 24.2239839,
                "lng": 90.4077741,
                "contributor_id": 2745,
                "contributor_name": "BESTSELLER",
                "notes": null
            },
            {
                "lat": 24.1996574,
                "lng": 90.48090979999999,
                "contributor_id": 11889,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 19188,
                "contributor_name": "Helly Hansen",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 2238,
                "contributor_name": "International Accord",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 11889,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 11889,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "notes": null
            },
            {
                "lat": 24.2592925,
                "lng": 90.3983004,
                "contributor_id": 2238,
                "contributor_name": "International Accord",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 2238,
                "contributor_name": "International Accord",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 3365,
                "contributor_name": "amfori",
                "notes": null
            },
            {
                "lat": 24.2592925,
                "lng": 90.3983004,
                "contributor_id": 2238,
                "contributor_name": "International Accord",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 20593,
                "contributor_name": "Climate TRACE",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 11889,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 20593,
                "contributor_name": "Climate TRACE",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 13389,
                "contributor_name": "Social & Labor Convergence Program (SLCP)",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 2144,
                "contributor_name": "Nirapon Inc.",
                "notes": null
            },
            {
                "lat": 24.1996574,
                "lng": 90.48090979999999,
                "contributor_id": 1342,
                "contributor_name": "Ralph Lauren Corporation",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 11889,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 13389,
                "contributor_name": "Social & Labor Convergence Program (SLCP)",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 6294,
                "contributor_name": "PVH",
                "notes": null
            },
            {
                "lat": 24.2532599,
                "lng": 90.3915452,
                "contributor_id": 8742,
                "contributor_name": "Target Corporation",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 26,
                "contributor_name": "Levi Strauss & Co.",
                "notes": null
            },
            {
                "lat": 24.2592925,
                "lng": 90.3983004,
                "contributor_id": 2238,
                "contributor_name": "International Accord",
                "notes": null
            },
            {
                "lat": 24.2592925,
                "lng": 90.3983004,
                "contributor_id": 4699,
                "contributor_name": "J.Crew Group",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 6597,
                "contributor_name": "Dekko ISHO [Public List]",
                "notes": null
            },
            {
                "lat": 24.2112968,
                "lng": 90.441039,
                "contributor_id": 5102,
                "contributor_name": "Better Cotton",
                "notes": null
            },
            {
                "lat": 24.2085878,
                "lng": 90.4493212,
                "contributor_id": 1237,
                "contributor_name": "Tom Tailor GmbH",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 1673,
                "contributor_name": "KIABI",
                "notes": null
            },
            {
                "lat": 24.2172542,
                "lng": 90.41390559999999,
                "contributor_id": 841,
                "contributor_name": "HEMA B.V.",
                "notes": null
            },
            {
                "lat": 24.2185381,
                "lng": 90.4127235,
                "contributor_id": 97,
                "contributor_name": "Fair Factories Clearinghouse",
                "notes": null
            },
            {
                "lat": 24.2112968,
                "lng": 90.441039,
                "contributor_id": 3757,
                "contributor_name": "Bangladesh Industrial Import Registration Certificate (IRC) [Public List]",
                "notes": null
            },
            {
                "lat": 24.2185381,
                "lng": 90.4127235,
                "contributor_id": 4402,
                "contributor_name": "Dekko Garments Ltd.",
                "notes": null
            },
            {
                "lat": 24.2112968,
                "lng": 90.441039,
                "contributor_id": 6294,
                "contributor_name": "PVH",
                "notes": null
            },
            {
                "lat": 24.2113921,
                "lng": 90.4408122,
                "contributor_id": 3126,
                "contributor_name": "Esprit",
                "notes": null
            },
            {
                "lat": 24.2112968,
                "lng": 90.441039,
                "contributor_id": 1237,
                "contributor_name": "Tom Tailor GmbH",
                "notes": null
            },
            {
                "lat": 24.2112968,
                "lng": 90.441039,
                "contributor_id": 1342,
                "contributor_name": "Ralph Lauren Corporation",
                "notes": null
            },
            {
                "lat": 24.2006941,
                "lng": 90.4736606,
                "contributor_id": 6294,
                "contributor_name": "PVH",
                "notes": null
            },
            {
                "lat": 24.2006941,
                "lng": 90.4736606,
                "contributor_id": 12108,
                "contributor_name": "VARNER AS",
                "notes": null
            },
            {
                "lat": 24.2006941,
                "lng": 90.4736606,
                "contributor_id": 841,
                "contributor_name": "HEMA B.V.",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 3394,
                "contributor_name": "Kontoor Brands, Inc. (KTB)",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 7745,
                "contributor_name": "RISE",
                "notes": null
            },
            {
                "lat": 24.2592925,
                "lng": 90.3983004,
                "contributor_id": 841,
                "contributor_name": "HEMA B.V.",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 1050,
                "contributor_name": "ZDHC Foundation",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 12108,
                "contributor_name": "VARNER AS",
                "notes": null
            },
            {
                "lat": 24.2592925,
                "lng": 90.3983004,
                "contributor_id": 1237,
                "contributor_name": "Tom Tailor GmbH",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 11889,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "notes": null
            },
            {
                "lat": 24.2112968,
                "lng": 90.441039,
                "contributor_id": 686,
                "contributor_name": "Worldly",
                "notes": null
            },
            {
                "lat": 24.2112968,
                "lng": 90.441039,
                "contributor_id": 686,
                "contributor_name": "Worldly",
                "notes": null
            },
            {
                "lat": 24.2592925,
                "lng": 90.3983004,
                "contributor_id": 2238,
                "contributor_name": "International Accord",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 686,
                "contributor_name": "Worldly",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 12108,
                "contributor_name": "VARNER AS",
                "notes": null
            },
            {
                "lat": 24.2206888,
                "lng": 90.41227169999999,
                "contributor_id": 13389,
                "contributor_name": "Social & Labor Convergence Program (SLCP)",
                "notes": null
            },
            {
                "lat": 24.1996574,
                "lng": 90.48090979999999,
                "contributor_id": 11889,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "notes": null
            },
            {
                "lat": 24.2532599,
                "lng": 90.3915452,
                "contributor_id": 205,
                "contributor_name": "Mapped in Bangladesh (MiB) - BRAC University",
                "notes": null
            }
        ],
        "is_closed": null,
        "activity_reports": [],
        "contributor_fields": [],
        "new_os_id": null,
        "has_inexact_coordinates": false,
        "extended_fields": {
            "name": [
                {
                    "id": 986511,
                    "is_verified": false,
                    "value": "Dekko Garments Ltd.",
                    "updated_at": "2024-01-29T04:41:06.456629Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": true,
                    "field_name": "name",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 4402,
                    "contributor_name": "Dekko Garments Ltd.",
                    "updated_at": "2023-01-22T14:39:15.048576Z",
                    "is_from_created_from": true
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 3394,
                    "contributor_name": "Kontoor Brands, Inc. (KTB)",
                    "updated_at": "2025-07-01T03:24:01.998936Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd",
                    "field_name": "name",
                    "contributor_id": 11651,
                    "contributor_name": "Wm Morrison Supermarkets Limited",
                    "updated_at": "2025-08-08T17:20:33.180902Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd",
                    "field_name": "name",
                    "contributor_id": 2144,
                    "contributor_name": "Nirapon Inc.",
                    "updated_at": "2025-10-10T21:20:19.496077Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 1673,
                    "contributor_name": "KIABI",
                    "updated_at": "2025-10-21T17:02:45.572414Z",
                    "is_from_created_from": false
                },
                {
                    "value": "DEKKO GARMENTS LTD",
                    "field_name": "name",
                    "contributor_id": 17853,
                    "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                    "updated_at": "2025-10-30T09:46:04.823793Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 6563,
                    "contributor_name": "Sainsbury's",
                    "updated_at": "2025-12-03T17:48:36.347207Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 12108,
                    "contributor_name": "VARNER AS",
                    "updated_at": "2025-12-03T18:22:54.757473Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2025-11-25T16:34:06.155260Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 1673,
                    "contributor_name": "KIABI",
                    "updated_at": "2026-03-26T03:25:19.398318Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 3365,
                    "contributor_name": "amfori",
                    "updated_at": "2026-04-08T09:12:11.035933Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 12266,
                    "contributor_name": "Tesco Stores Ltd",
                    "updated_at": "2026-01-07T08:09:24.627717Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 2745,
                    "contributor_name": "BESTSELLER",
                    "updated_at": "2026-05-28T02:34:26.017209Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-09T16:15:12.360247Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd",
                    "field_name": "name",
                    "contributor_id": 19188,
                    "contributor_name": "Helly Hansen",
                    "updated_at": "2026-01-27T13:40:16.579843Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2026-04-03T04:44:09.578040Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-23T17:13:44.801510Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-22T14:14:23.239876Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2024-06-04T04:27:25.796956Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2026-04-17T04:05:25.788256Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 3365,
                    "contributor_name": "amfori",
                    "updated_at": "2026-06-03T10:34:54.776576Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2026-03-13T13:57:32.198883Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 20593,
                    "contributor_name": "Climate TRACE",
                    "updated_at": "2026-04-18T01:03:55.273582Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-17T20:04:06.136260Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 20593,
                    "contributor_name": "Climate TRACE",
                    "updated_at": "2026-04-18T02:03:56.109833Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 13389,
                    "contributor_name": "Social & Labor Convergence Program (SLCP)",
                    "updated_at": "2026-04-17T06:35:34.603332Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd",
                    "field_name": "name",
                    "contributor_id": 2144,
                    "contributor_name": "Nirapon Inc.",
                    "updated_at": "2026-05-14T20:54:17.597126Z",
                    "is_from_created_from": false
                },
                {
                    "value": "DEKKO GARMENTS LIMITED",
                    "field_name": "name",
                    "contributor_id": 1342,
                    "contributor_name": "Ralph Lauren Corporation",
                    "updated_at": "2026-05-20T17:46:35.171352Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-23T18:51:24.893903Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 13389,
                    "contributor_name": "Social & Labor Convergence Program (SLCP)",
                    "updated_at": "2026-04-16T10:11:40.443485Z",
                    "is_from_created_from": false
                },
                {
                    "value": "DEKKO GARMENTS LIMITED",
                    "field_name": "name",
                    "contributor_id": 6294,
                    "contributor_name": "PVH",
                    "updated_at": "2026-05-27T17:38:58.573347Z",
                    "is_from_created_from": false
                },
                {
                    "value": "DEKKO GARMENTS LTD.",
                    "field_name": "name",
                    "contributor_id": 8742,
                    "contributor_name": "Target Corporation",
                    "updated_at": "2026-06-25T19:20:59.918310Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 26,
                    "contributor_name": "Levi Strauss & Co.",
                    "updated_at": "2026-06-26T16:51:30.071025Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2026-06-30T18:32:04.086915Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd",
                    "field_name": "name",
                    "contributor_id": 4699,
                    "contributor_name": "J.Crew Group",
                    "updated_at": "2026-06-30T20:25:02.560500Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 6597,
                    "contributor_name": "Dekko ISHO [Public List]",
                    "updated_at": "2024-07-15T18:40:39.813671Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd",
                    "field_name": "name",
                    "contributor_id": 5102,
                    "contributor_name": "Better Cotton",
                    "updated_at": "2022-01-27T17:41:06.088215Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 1237,
                    "contributor_name": "Tom Tailor GmbH",
                    "updated_at": "2022-03-04T07:41:04.577912Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 1673,
                    "contributor_name": "KIABI",
                    "updated_at": "2025-02-10T18:34:18.443433Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 841,
                    "contributor_name": "HEMA B.V.",
                    "updated_at": "2022-11-02T11:06:39.579803Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 97,
                    "contributor_name": "Fair Factories Clearinghouse",
                    "updated_at": "2022-10-23T18:16:19.520220Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 3757,
                    "contributor_name": "Bangladesh Industrial Import Registration Certificate (IRC) [Public List]",
                    "updated_at": "2022-10-25T16:16:45.014936Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 6294,
                    "contributor_name": "PVH",
                    "updated_at": "2023-01-24T02:02:54.299252Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd",
                    "field_name": "name",
                    "contributor_id": 3126,
                    "contributor_name": "Esprit",
                    "updated_at": "2023-03-31T14:49:13.526431Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 1237,
                    "contributor_name": "Tom Tailor GmbH",
                    "updated_at": "2023-04-04T18:26:24.289679Z",
                    "is_from_created_from": false
                },
                {
                    "value": "DEKKO GARMENTS LIMITED",
                    "field_name": "name",
                    "contributor_id": 1342,
                    "contributor_name": "Ralph Lauren Corporation",
                    "updated_at": "2023-04-05T17:12:18.590465Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 6294,
                    "contributor_name": "PVH",
                    "updated_at": "2023-08-30T16:41:58.072749Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 12108,
                    "contributor_name": "VARNER AS",
                    "updated_at": "2023-09-15T20:55:29.973469Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 841,
                    "contributor_name": "HEMA B.V.",
                    "updated_at": "2023-11-13T14:17:42.419424Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 3394,
                    "contributor_name": "Kontoor Brands, Inc. (KTB)",
                    "updated_at": "2025-02-20T03:19:55.761047Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd",
                    "field_name": "name",
                    "contributor_id": 7745,
                    "contributor_name": "RISE",
                    "updated_at": "2024-01-26T19:30:12.772054Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 841,
                    "contributor_name": "HEMA B.V.",
                    "updated_at": "2024-12-02T18:03:17.252409Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 1050,
                    "contributor_name": "ZDHC Foundation",
                    "updated_at": "2024-03-27T01:14:50.822943Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 12108,
                    "contributor_name": "VARNER AS",
                    "updated_at": "2025-01-23T03:00:06.342919Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 1237,
                    "contributor_name": "Tom Tailor GmbH",
                    "updated_at": "2024-04-02T23:43:20.272385Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2025-01-09T10:21:19.118035Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 686,
                    "contributor_name": "Worldly",
                    "updated_at": "2024-05-24T02:12:57.266842Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 686,
                    "contributor_name": "Worldly",
                    "updated_at": "2024-05-24T02:13:58.342697Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2024-05-24T05:32:23.006577Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 686,
                    "contributor_name": "Worldly",
                    "updated_at": "2024-05-25T10:15:11.808687Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Limited",
                    "field_name": "name",
                    "contributor_id": 12108,
                    "contributor_name": "VARNER AS",
                    "updated_at": "2025-04-01T12:44:18.038440Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 13389,
                    "contributor_name": "Social & Labor Convergence Program (SLCP)",
                    "updated_at": "2025-04-20T04:32:36.332465Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2025-05-01T00:48:42.150760Z",
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd.",
                    "field_name": "name",
                    "contributor_id": 205,
                    "contributor_name": "Mapped in Bangladesh (MiB) - BRAC University",
                    "updated_at": "2025-06-24T23:52:05.083072Z",
                    "is_from_created_from": false
                }
            ],
            "address": [
                {
                    "id": 986512,
                    "is_verified": false,
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "updated_at": "2024-01-29T04:41:06.481245Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": true,
                    "field_name": "address",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 4402,
                    "contributor_name": "Dekko Garments Ltd.",
                    "updated_at": "2023-01-22T14:39:15.048576Z",
                    "is_from_claim": false,
                    "is_from_created_from": true
                },
                {
                    "value": "Mawna, Sreepur, Gazipur, Dhaka, Bangladesh",
                    "field_name": "address",
                    "contributor_id": 3394,
                    "contributor_name": "Kontoor Brands, Inc. (KTB)",
                    "updated_at": "2025-07-01T03:24:01.998936Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 11651,
                    "contributor_name": "Wm Morrison Supermarkets Limited",
                    "updated_at": "2025-08-08T17:20:33.180902Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 2144,
                    "contributor_name": "Nirapon Inc.",
                    "updated_at": "2025-10-10T21:20:19.496077Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur. Bangladesh",
                    "field_name": "address",
                    "contributor_id": 1673,
                    "contributor_name": "KIABI",
                    "updated_at": "2025-10-21T17:02:45.572414Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur, Dhaka",
                    "field_name": "address",
                    "contributor_id": 17853,
                    "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                    "updated_at": "2025-10-30T09:46:04.823793Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur, Nayanpur, Sreepur, Gazipur, GazipurBangladesh",
                    "field_name": "address",
                    "contributor_id": 6563,
                    "contributor_name": "Sainsbury's",
                    "updated_at": "2025-12-03T17:48:36.347207Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 12108,
                    "contributor_name": "VARNER AS",
                    "updated_at": "2025-12-03T18:22:54.757473Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, Gazipur.",
                    "field_name": "address",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2025-11-25T16:34:06.155260Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur. Bangladesh",
                    "field_name": "address",
                    "contributor_id": 1673,
                    "contributor_name": "KIABI",
                    "updated_at": "2026-03-26T03:25:19.398318Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 3365,
                    "contributor_name": "amfori",
                    "updated_at": "2026-04-08T09:12:11.035933Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur, Dhaka",
                    "field_name": "address",
                    "contributor_id": 12266,
                    "contributor_name": "Tesco Stores Ltd",
                    "updated_at": "2026-01-07T08:09:24.627717Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, 1740, Gazipur",
                    "field_name": "address",
                    "contributor_id": 2745,
                    "contributor_name": "BESTSELLER",
                    "updated_at": "2026-05-28T02:34:26.017209Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur, Gazipur, Gazipur, 1740",
                    "field_name": "address",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-09T16:15:12.360247Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur - 1740, Bangladesh",
                    "field_name": "address",
                    "contributor_id": 19188,
                    "contributor_name": "Helly Hansen",
                    "updated_at": "2026-01-27T13:40:16.579843Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2026-04-03T04:44:09.578040Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-23T17:13:44.801510Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-22T14:14:23.239876Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, Gazipur.",
                    "field_name": "address",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2024-06-04T04:27:25.796956Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2026-04-17T04:05:25.788256Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 3365,
                    "contributor_name": "amfori",
                    "updated_at": "2026-06-03T10:34:54.776576Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, Gazipur.",
                    "field_name": "address",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2026-03-13T13:57:32.198883Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 20593,
                    "contributor_name": "Climate TRACE",
                    "updated_at": "2026-04-18T01:03:55.273582Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-17T20:04:06.136260Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 20593,
                    "contributor_name": "Climate TRACE",
                    "updated_at": "2026-04-18T02:03:56.109833Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 13389,
                    "contributor_name": "Social & Labor Convergence Program (SLCP)",
                    "updated_at": "2026-04-17T06:35:34.603332Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 2144,
                    "contributor_name": "Nirapon Inc.",
                    "updated_at": "2026-05-14T20:54:17.597126Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "MAWNA, SREEPUR, GAZIPUR, MAWNA UTTARPARA, GAZIPUR, DHAKA",
                    "field_name": "address",
                    "contributor_id": 1342,
                    "contributor_name": "Ralph Lauren Corporation",
                    "updated_at": "2026-05-20T17:46:35.171352Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2026-04-23T18:51:24.893903Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 13389,
                    "contributor_name": "Social & Labor Convergence Program (SLCP)",
                    "updated_at": "2026-04-16T10:11:40.443485Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Dhaka Gazipur 1703",
                    "field_name": "address",
                    "contributor_id": 6294,
                    "contributor_name": "PVH",
                    "updated_at": "2026-05-27T17:38:58.573347Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Dekko Garments Ltd, Mawna, Sreepur\nDhaka zila\nGazipur\n1740",
                    "field_name": "address",
                    "contributor_id": 8742,
                    "contributor_name": "Target Corporation",
                    "updated_at": "2026-06-25T19:20:59.918310Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "MAWNA, SREEPUR, GAZIPUR, Dhaka",
                    "field_name": "address",
                    "contributor_id": 26,
                    "contributor_name": "Levi Strauss & Co.",
                    "updated_at": "2026-06-26T16:51:30.071025Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, Gazipur., Gazipur",
                    "field_name": "address",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2026-06-30T18:32:04.086915Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur BD, GAZIPUR SADAR, Bangladesh",
                    "field_name": "address",
                    "contributor_id": 4699,
                    "contributor_name": "J.Crew Group",
                    "updated_at": "2026-06-30T20:25:02.560500Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Noyanpur Bazar Road, Mawna Union, Bangladesh",
                    "field_name": "address",
                    "contributor_id": 6597,
                    "contributor_name": "Dekko ISHO [Public List]",
                    "updated_at": "2024-07-15T18:40:39.813671Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna,Sreepur, Gazipur.",
                    "field_name": "address",
                    "contributor_id": 5102,
                    "contributor_name": "Better Cotton",
                    "updated_at": "2022-01-27T17:41:06.088215Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur",
                    "field_name": "address",
                    "contributor_id": 1237,
                    "contributor_name": "Tom Tailor GmbH",
                    "updated_at": "2022-03-04T07:41:04.577912Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur. Bangladesh",
                    "field_name": "address",
                    "contributor_id": 1673,
                    "contributor_name": "KIABI",
                    "updated_at": "2025-02-10T18:34:18.443433Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, 1703, Gazipur",
                    "field_name": "address",
                    "contributor_id": 841,
                    "contributor_name": "HEMA B.V.",
                    "updated_at": "2022-11-02T11:06:39.579803Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "MAWNA, SREEPUR, GAZIPUR, Dhaka 1740",
                    "field_name": "address",
                    "contributor_id": 97,
                    "contributor_name": "Fair Factories Clearinghouse",
                    "updated_at": "2022-10-23T18:16:19.520220Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur.",
                    "field_name": "address",
                    "contributor_id": 3757,
                    "contributor_name": "Bangladesh Industrial Import Registration Certificate (IRC) [Public List]",
                    "updated_at": "2022-10-25T16:16:45.014936Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur",
                    "field_name": "address",
                    "contributor_id": 6294,
                    "contributor_name": "PVH",
                    "updated_at": "2023-01-24T02:02:54.299252Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, 1740, Sreepur, Gazipur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 3126,
                    "contributor_name": "Esprit",
                    "updated_at": "2023-03-31T14:49:13.526431Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur",
                    "field_name": "address",
                    "contributor_id": 1237,
                    "contributor_name": "Tom Tailor GmbH",
                    "updated_at": "2023-04-04T18:26:24.289679Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "MAWNA, SREEPUR, GAZIPUR,MAWNA UTTARPARA,GAZIPUR, DHAKA,BANGLADESH",
                    "field_name": "address",
                    "contributor_id": 1342,
                    "contributor_name": "Ralph Lauren Corporation",
                    "updated_at": "2023-04-05T17:12:18.590465Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur,Dhaka Gazipur",
                    "field_name": "address",
                    "contributor_id": 6294,
                    "contributor_name": "PVH",
                    "updated_at": "2023-08-30T16:41:58.072749Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 12108,
                    "contributor_name": "VARNER AS",
                    "updated_at": "2023-09-15T20:55:29.973469Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, 1703, Gazipur",
                    "field_name": "address",
                    "contributor_id": 841,
                    "contributor_name": "HEMA B.V.",
                    "updated_at": "2023-11-13T14:17:42.419424Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur, Dhaka, Bangladesh",
                    "field_name": "address",
                    "contributor_id": 3394,
                    "contributor_name": "Kontoor Brands, Inc. (KTB)",
                    "updated_at": "2025-02-20T03:19:55.761047Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, Gazipur, Mawna Uttarpara, Gazipur 1703, Dhaka",
                    "field_name": "address",
                    "contributor_id": 7745,
                    "contributor_name": "RISE",
                    "updated_at": "2024-01-26T19:30:12.772054Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur",
                    "field_name": "address",
                    "contributor_id": 841,
                    "contributor_name": "HEMA B.V.",
                    "updated_at": "2024-12-02T18:03:17.252409Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740.",
                    "field_name": "address",
                    "contributor_id": 1050,
                    "contributor_name": "ZDHC Foundation",
                    "updated_at": "2024-03-27T01:14:50.822943Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 12108,
                    "contributor_name": "VARNER AS",
                    "updated_at": "2025-01-23T03:00:06.342919Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, 1740 Gazipur, Bangladesh",
                    "field_name": "address",
                    "contributor_id": 1237,
                    "contributor_name": "Tom Tailor GmbH",
                    "updated_at": "2024-04-02T23:43:20.272385Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2025-01-09T10:21:19.118035Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna - Sreepur Rd, Sreepur, Bangladesh",
                    "field_name": "address",
                    "contributor_id": 686,
                    "contributor_name": "Worldly",
                    "updated_at": "2024-05-24T02:12:57.266842Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna - Sreepur Rd, Sreepur, Bangladesh",
                    "field_name": "address",
                    "contributor_id": 686,
                    "contributor_name": "Worldly",
                    "updated_at": "2024-05-24T02:13:58.342697Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Nayanpur, Mawna, Sreepur, Gazipur.",
                    "field_name": "address",
                    "contributor_id": 2238,
                    "contributor_name": "International Accord",
                    "updated_at": "2024-05-24T05:32:23.006577Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 686,
                    "contributor_name": "Worldly",
                    "updated_at": "2024-05-25T10:15:11.808687Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur",
                    "field_name": "address",
                    "contributor_id": 12108,
                    "contributor_name": "VARNER AS",
                    "updated_at": "2025-04-01T12:44:18.038440Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 13389,
                    "contributor_name": "Social & Labor Convergence Program (SLCP)",
                    "updated_at": "2025-04-20T04:32:36.332465Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "Mawna, Sreepur, Gazipur, Gazipur, Gazipur 1740",
                    "field_name": "address",
                    "contributor_id": 11889,
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "updated_at": "2025-05-01T00:48:42.150760Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                },
                {
                    "value": "(Ground Floor), Dekko Garments Road, Nayanpur, Sreepur, Gazipur-1740",
                    "field_name": "address",
                    "contributor_id": 205,
                    "contributor_name": "Mapped in Bangladesh (MiB) - BRAC University",
                    "updated_at": "2025-06-24T23:52:05.083072Z",
                    "is_from_claim": false,
                    "is_from_created_from": false
                }
            ],
            "number_of_workers": [
                {
                    "id": 335738,
                    "is_verified": false,
                    "value": {
                        "max": 5300,
                        "min": 5300
                    },
                    "updated_at": "2024-01-29T04:41:06.508044Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": true,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4858926,
                    "is_verified": false,
                    "value": {
                        "max": 5005,
                        "min": 5005
                    },
                    "updated_at": "2025-12-03T18:23:10.136801Z",
                    "contributor_name": "VARNER AS",
                    "contributor_id": 12108,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3161616,
                    "is_verified": false,
                    "value": {
                        "max": 5005,
                        "min": 5005
                    },
                    "updated_at": "2025-04-01T12:44:27.380240Z",
                    "contributor_name": "VARNER AS",
                    "contributor_id": 12108,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3095490,
                    "is_verified": false,
                    "value": {
                        "max": 5005,
                        "min": 5005
                    },
                    "updated_at": "2025-01-23T03:00:20.186681Z",
                    "contributor_name": "VARNER AS",
                    "contributor_id": 12108,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 641726,
                    "is_verified": false,
                    "value": {
                        "max": 5005,
                        "min": 5005
                    },
                    "updated_at": "2023-09-15T20:56:42.648565Z",
                    "contributor_name": "Varner AS",
                    "contributor_id": 882,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3048905,
                    "is_verified": false,
                    "value": {
                        "max": 1924,
                        "min": 1924
                    },
                    "updated_at": "2024-12-02T18:03:42.158568Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 730410,
                    "is_verified": false,
                    "value": {
                        "max": 1924,
                        "min": 1924
                    },
                    "updated_at": "2023-11-13T14:19:16.547659Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 244451,
                    "is_verified": false,
                    "value": {
                        "max": 1924,
                        "min": 1924
                    },
                    "updated_at": "2022-11-02T11:07:56.007017Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6248374,
                    "is_verified": false,
                    "value": {
                        "max": 6329,
                        "min": 6329
                    },
                    "updated_at": "2026-03-13T13:58:51.146521Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4608886,
                    "is_verified": false,
                    "value": {
                        "max": 6329,
                        "min": 6329
                    },
                    "updated_at": "2025-11-25T16:34:57.289496Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3752263,
                    "is_verified": false,
                    "value": {
                        "max": 10,
                        "min": 0
                    },
                    "updated_at": "2025-07-01T03:24:17.510395Z",
                    "contributor_name": "Kontoor Brands, Inc. (KTB)",
                    "contributor_id": 3394,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3132306,
                    "is_verified": false,
                    "value": {
                        "max": 10,
                        "min": 0
                    },
                    "updated_at": "2025-02-20T03:20:13.260482Z",
                    "contributor_name": "Kontoor Brands, Inc. (KTB)",
                    "contributor_id": 3394,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1728304,
                    "is_verified": false,
                    "value": {
                        "max": 2300,
                        "min": 2300
                    },
                    "updated_at": "2024-06-04T04:28:27.806231Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1451406,
                    "is_verified": false,
                    "value": {
                        "max": 2300,
                        "min": 2300
                    },
                    "updated_at": "2024-05-24T05:33:55.853999Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6469869,
                    "is_verified": false,
                    "value": {
                        "max": 7057,
                        "min": 7057
                    },
                    "updated_at": "2026-06-30T18:33:34.796932Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6461688,
                    "is_verified": false,
                    "value": {
                        "max": 10000,
                        "min": 5000
                    },
                    "updated_at": "2026-06-26T16:51:48.654754Z",
                    "contributor_name": "Levi Strauss & Co.",
                    "contributor_id": 26,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6401772,
                    "is_verified": false,
                    "value": {
                        "max": 10000,
                        "min": 5001
                    },
                    "updated_at": "2026-05-28T02:34:53.554297Z",
                    "contributor_name": "BESTSELLER",
                    "contributor_id": 2745,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6427759,
                    "is_verified": false,
                    "value": {
                        "max": 5606,
                        "min": 5606
                    },
                    "updated_at": "2026-05-20T17:46:55.611736Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6074466,
                    "is_verified": false,
                    "value": {
                        "max": 5506,
                        "min": 5506
                    },
                    "updated_at": "2026-01-27T13:40:18.412168Z",
                    "contributor_name": "Helly Hansen",
                    "contributor_id": 19188,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4834674,
                    "is_verified": false,
                    "value": {
                        "max": 121,
                        "min": 2
                    },
                    "updated_at": "2025-12-03T17:49:07.528011Z",
                    "contributor_name": "Sainsbury's",
                    "contributor_id": 6563,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4689928,
                    "is_verified": false,
                    "value": {
                        "max": 4300,
                        "min": 4300
                    },
                    "updated_at": "2025-10-30T09:46:04.890168Z",
                    "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                    "contributor_id": 17853,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4559705,
                    "is_verified": false,
                    "value": {
                        "max": 6000,
                        "min": 6000
                    },
                    "updated_at": "2025-10-10T21:20:43.824913Z",
                    "contributor_name": "Nirapon Inc.",
                    "contributor_id": 2144,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3724321,
                    "is_verified": false,
                    "value": {
                        "max": 5316,
                        "min": 5316
                    },
                    "updated_at": "2025-06-24T23:52:05.131544Z",
                    "contributor_name": "Mapped In Bangladesh (MiB) - Brac University",
                    "contributor_id": 10707,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3582801,
                    "is_verified": false,
                    "value": {
                        "max": 4957,
                        "min": 4957
                    },
                    "updated_at": "2025-05-23T16:37:31.622407Z",
                    "contributor_name": "a Brand / Retailer",
                    "contributor_id": null,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3473245,
                    "is_verified": false,
                    "value": {
                        "max": 5600,
                        "min": 5600
                    },
                    "updated_at": "2025-05-01T00:49:58.556266Z",
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "contributor_id": 11889,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3079731,
                    "is_verified": false,
                    "value": {
                        "max": 5500,
                        "min": 5500
                    },
                    "updated_at": "2025-01-09T10:24:26.979811Z",
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "contributor_id": 11889,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1102126,
                    "is_verified": false,
                    "value": {
                        "max": 6000,
                        "min": 5501
                    },
                    "updated_at": "2024-04-02T23:43:21.902021Z",
                    "contributor_name": "Tom Tailor GmbH",
                    "contributor_id": 1237,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 986385,
                    "is_verified": false,
                    "value": {
                        "max": 2259,
                        "min": 2259
                    },
                    "updated_at": "2024-01-26T19:30:14.596902Z",
                    "contributor_name": "RISE",
                    "contributor_id": 7745,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 605886,
                    "is_verified": false,
                    "value": {
                        "max": 1001,
                        "min": 1001
                    },
                    "updated_at": "2023-08-30T16:43:41.109759Z",
                    "contributor_name": "PVH",
                    "contributor_id": 715,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 393397,
                    "is_verified": false,
                    "value": {
                        "max": 5000,
                        "min": 1001
                    },
                    "updated_at": "2023-04-05T17:12:36.961261Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 385975,
                    "is_verified": false,
                    "value": {
                        "max": 5000,
                        "min": 4501
                    },
                    "updated_at": "2023-04-04T18:26:27.499377Z",
                    "contributor_name": "Tom Tailor GmbH",
                    "contributor_id": 1237,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 372748,
                    "is_verified": false,
                    "value": {
                        "max": 5,
                        "min": 1
                    },
                    "updated_at": "2023-03-31T14:49:41.306213Z",
                    "contributor_name": "Esprit",
                    "contributor_id": 3126,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 318714,
                    "is_verified": false,
                    "value": {
                        "max": 4800,
                        "min": 4800
                    },
                    "updated_at": "2023-01-20T00:22:49.146024Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6590,
                    "is_verified": false,
                    "value": {
                        "max": 3000,
                        "min": 2501
                    },
                    "updated_at": "2022-03-04T07:41:05.314440Z",
                    "contributor_name": "Tom Tailor [Public List]",
                    "contributor_id": 913,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "number_of_workers",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                }
            ],
            "native_language_name": [
                {
                    "id": 986513,
                    "is_verified": false,
                    "value": "Dekko Garments Ltd.",
                    "updated_at": "2024-01-29T04:41:06.531850Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": true,
                    "field_name": "native_language_name",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                }
            ],
            "facility_type": [
                {
                    "id": 335740,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "cut & sew",
                            "embroidery",
                            "final product assembly",
                            "finishing"
                        ],
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Cut & Sew"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Textile or Material Production",
                                "Embroidery"
                            ],
                            [
                                "FACILITY_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Final Product Assembly"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Printing, Product Dyeing and Laundering",
                                "Finishing"
                            ]
                        ]
                    },
                    "updated_at": "2024-01-29T04:41:06.569889Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": true,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6469870,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Ready Made Garment",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Ready Made Garment"
                            ]
                        ]
                    },
                    "updated_at": "2026-06-30T18:33:34.833003Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6248375,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Ready Made Garment",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Ready Made Garment"
                            ]
                        ]
                    },
                    "updated_at": "2026-03-13T13:58:51.184928Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4608887,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Ready Made Garment",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Ready Made Garment"
                            ]
                        ]
                    },
                    "updated_at": "2025-11-25T16:34:57.325177Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4689930,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Ready Made Garment",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Ready Made Garment"
                            ]
                        ]
                    },
                    "updated_at": "2025-10-30T09:46:04.958404Z",
                    "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                    "contributor_id": 17853,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6427761,
                    "is_verified": false,
                    "value": {
                        "raw_values": "MANUFACTURING",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Manufacturing"
                            ]
                        ]
                    },
                    "updated_at": "2026-05-20T17:46:55.731723Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3582804,
                    "is_verified": false,
                    "value": {
                        "raw_values": "MANUFACTURING",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Manufacturing"
                            ]
                        ]
                    },
                    "updated_at": "2025-05-23T16:37:31.711908Z",
                    "contributor_name": "a Brand / Retailer",
                    "contributor_id": null,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1102128,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Final Product Assembly",
                        "matched_values": [
                            [
                                "FACILITY_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Final Product Assembly"
                            ]
                        ]
                    },
                    "updated_at": "2024-04-02T23:43:21.936547Z",
                    "contributor_name": "Tom Tailor GmbH",
                    "contributor_id": 1237,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 393400,
                    "is_verified": false,
                    "value": {
                        "raw_values": "MANUFACTURING",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Manufacturing"
                            ]
                        ]
                    },
                    "updated_at": "2023-04-05T17:12:36.998477Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 385976,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Final Product Assembly",
                        "matched_values": [
                            [
                                "FACILITY_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Final Product Assembly"
                            ]
                        ]
                    },
                    "updated_at": "2023-04-04T18:26:27.512930Z",
                    "contributor_name": "Tom Tailor GmbH",
                    "contributor_id": 1237,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 372750,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Final Product Assembly",
                        "matched_values": [
                            [
                                "FACILITY_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Final Product Assembly"
                            ]
                        ]
                    },
                    "updated_at": "2023-03-31T14:49:41.332022Z",
                    "contributor_name": "Esprit",
                    "contributor_id": 3126,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6461690,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Cut & Sew",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Cut & Sew"
                            ]
                        ]
                    },
                    "updated_at": "2026-06-26T16:51:48.724179Z",
                    "contributor_name": "Levi Strauss & Co.",
                    "contributor_id": 26,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3724323,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Cutting|Sewing|Finishing and Packing|Embroidery",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Sewing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "FUZZY",
                                "Warehousing / Distribution",
                                "Packing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Textile or Material Production",
                                "Embroidery"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Cutting"
                            ]
                        ]
                    },
                    "updated_at": "2025-06-24T23:52:05.193072Z",
                    "contributor_name": "Mapped In Bangladesh (MiB) - Brac University",
                    "contributor_id": 10707,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3048907,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Assembling|Packing|Quality control",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Packing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Quality control"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Assembling"
                            ]
                        ]
                    },
                    "updated_at": "2024-12-02T18:03:42.219129Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1728309,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Factory",
                        "matched_values": [
                            [
                                null,
                                null,
                                null,
                                null
                            ]
                        ]
                    },
                    "updated_at": "2024-06-04T04:28:27.844357Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 730413,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Assembling|Packing|Quality control",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Assembling"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Packing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Quality control"
                            ]
                        ]
                    },
                    "updated_at": "2023-11-13T14:19:16.725293Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 605887,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Level 1",
                        "matched_values": [
                            [
                                null,
                                null,
                                null,
                                null
                            ]
                        ]
                    },
                    "updated_at": "2023-08-30T16:43:41.161736Z",
                    "contributor_name": "PVH",
                    "contributor_id": 715,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 318717,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Cutting|Embroidery|Sewing|Finishing|Packing",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Cutting"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Embroidery"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Sewing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Finishing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Packing"
                            ]
                        ]
                    },
                    "updated_at": "2023-01-20T00:22:49.219738Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 244453,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Assembling|Packing|Quality Control",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Assembling"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Packing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Quality Control"
                            ]
                        ]
                    },
                    "updated_at": "2022-11-02T11:07:56.054744Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "facility_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                }
            ],
            "processing_type": [
                {
                    "id": 335739,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "cut & sew",
                            "embroidery",
                            "final product assembly",
                            "finishing"
                        ],
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Cut & Sew"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Textile or Material Production",
                                "Embroidery"
                            ],
                            [
                                "FACILITY_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Final Product Assembly"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Printing, Product Dyeing and Laundering",
                                "Finishing"
                            ]
                        ]
                    },
                    "updated_at": "2024-01-29T04:41:06.551064Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": true,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6469871,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Ready Made Garment",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Ready Made Garment"
                            ]
                        ]
                    },
                    "updated_at": "2026-06-30T18:33:34.868981Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6248376,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Ready Made Garment",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Ready Made Garment"
                            ]
                        ]
                    },
                    "updated_at": "2026-03-13T13:58:51.223829Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4608888,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Ready Made Garment",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Ready Made Garment"
                            ]
                        ]
                    },
                    "updated_at": "2025-11-25T16:34:57.359064Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4689931,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Ready Made Garment",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Ready Made Garment"
                            ]
                        ]
                    },
                    "updated_at": "2025-10-30T09:46:04.992213Z",
                    "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                    "contributor_id": 17853,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6427762,
                    "is_verified": false,
                    "value": {
                        "raw_values": "MANUFACTURING",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Manufacturing"
                            ]
                        ]
                    },
                    "updated_at": "2026-05-20T17:46:55.791187Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3582805,
                    "is_verified": false,
                    "value": {
                        "raw_values": "MANUFACTURING",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Manufacturing"
                            ]
                        ]
                    },
                    "updated_at": "2025-05-23T16:37:31.741360Z",
                    "contributor_name": "a Brand / Retailer",
                    "contributor_id": null,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1102129,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Final Product Assembly",
                        "matched_values": [
                            [
                                "FACILITY_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Final Product Assembly"
                            ]
                        ]
                    },
                    "updated_at": "2024-04-02T23:43:21.953192Z",
                    "contributor_name": "Tom Tailor GmbH",
                    "contributor_id": 1237,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 393401,
                    "is_verified": false,
                    "value": {
                        "raw_values": "MANUFACTURING",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Manufacturing"
                            ]
                        ]
                    },
                    "updated_at": "2023-04-05T17:12:37.011196Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 385977,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Final Product Assembly",
                        "matched_values": [
                            [
                                "FACILITY_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Final Product Assembly"
                            ]
                        ]
                    },
                    "updated_at": "2023-04-04T18:26:27.525841Z",
                    "contributor_name": "Tom Tailor GmbH",
                    "contributor_id": 1237,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 372751,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Final Product Assembly",
                        "matched_values": [
                            [
                                "FACILITY_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Final Product Assembly"
                            ]
                        ]
                    },
                    "updated_at": "2023-03-31T14:49:41.343569Z",
                    "contributor_name": "Esprit",
                    "contributor_id": 3126,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6461691,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Cut & Sew",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Cut & Sew"
                            ]
                        ]
                    },
                    "updated_at": "2026-06-26T16:51:48.758450Z",
                    "contributor_name": "Levi Strauss & Co.",
                    "contributor_id": 26,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3724324,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Cutting|Sewing|Finishing and Packing|Embroidery",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Sewing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "FUZZY",
                                "Warehousing / Distribution",
                                "Packing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Textile or Material Production",
                                "Embroidery"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "EXACT",
                                "Final Product Assembly",
                                "Cutting"
                            ]
                        ]
                    },
                    "updated_at": "2025-06-24T23:52:05.221083Z",
                    "contributor_name": "Mapped In Bangladesh (MiB) - Brac University",
                    "contributor_id": 10707,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3048908,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Assembling|Packing|Quality control",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Packing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Quality control"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Assembling"
                            ]
                        ]
                    },
                    "updated_at": "2024-12-02T18:03:42.248581Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1728311,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Factory",
                        "matched_values": [
                            [
                                null,
                                null,
                                null,
                                null
                            ]
                        ]
                    },
                    "updated_at": "2024-06-04T04:28:27.863035Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 730414,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Assembling|Packing|Quality control",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Assembling"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Packing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Quality control"
                            ]
                        ]
                    },
                    "updated_at": "2023-11-13T14:19:16.811310Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 605888,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Level 1",
                        "matched_values": [
                            [
                                null,
                                null,
                                null,
                                null
                            ]
                        ]
                    },
                    "updated_at": "2023-08-30T16:43:41.212693Z",
                    "contributor_name": "PVH",
                    "contributor_id": 715,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 318718,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Cutting|Embroidery|Sewing|Finishing|Packing",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Cutting"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Embroidery"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Sewing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Finishing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Packing"
                            ]
                        ]
                    },
                    "updated_at": "2023-01-20T00:22:49.238485Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 244454,
                    "is_verified": false,
                    "value": {
                        "raw_values": "Assembling|Packing|Quality Control",
                        "matched_values": [
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Assembling"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Packing"
                            ],
                            [
                                "PROCESSING_TYPE",
                                "SKIPPED_MATCHING",
                                null,
                                "Quality Control"
                            ]
                        ]
                    },
                    "updated_at": "2022-11-02T11:07:56.077098Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "processing_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                }
            ],
            "product_type": [
                {
                    "id": 335742,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "All types of Woven Bottoms & Tops"
                        ]
                    },
                    "updated_at": "2024-01-29T04:41:06.628268Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": true,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3582803,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Wovens"
                        ]
                    },
                    "updated_at": "2025-05-23T16:37:31.682667Z",
                    "contributor_name": "a Brand / Retailer",
                    "contributor_id": null,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1959032,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Ready Made Garment"
                        ]
                    },
                    "updated_at": "2024-07-15T18:40:39.923191Z",
                    "contributor_name": "Dekko ISHO [Public List]",
                    "contributor_id": 6597,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1728305,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Ready Made Garment"
                        ]
                    },
                    "updated_at": "2024-06-04T04:28:27.825403Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 393399,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Wovens"
                        ]
                    },
                    "updated_at": "2023-04-05T17:12:36.986280Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4689929,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Knitwear"
                        ]
                    },
                    "updated_at": "2025-10-30T09:46:04.924550Z",
                    "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                    "contributor_id": 17853,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3724322,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Dress Shirts/ Shirts MB",
                            "Jackets",
                            "Jeans",
                            "Ladies Shirts/ Blouses & Fashion Wears",
                            "Pants",
                            "Shorts",
                            "Trousers"
                        ]
                    },
                    "updated_at": "2025-06-24T23:52:05.163727Z",
                    "contributor_name": "Mapped In Bangladesh (MiB) - Brac University",
                    "contributor_id": 10707,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1451407,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "RMG"
                        ]
                    },
                    "updated_at": "2024-05-24T05:33:55.883407Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 730412,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Textile"
                        ]
                    },
                    "updated_at": "2023-11-13T14:19:16.668322Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 318716,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Woven Bottoms",
                            "Woven Tops"
                        ]
                    },
                    "updated_at": "2023-01-20T00:22:49.200577Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6592,
                    "is_verified": false,
                    "value": {
                        "raw_values": [
                            "Woven"
                        ]
                    },
                    "updated_at": "2022-03-04T07:41:05.333121Z",
                    "contributor_name": "Tom Tailor [Public List]",
                    "contributor_id": 913,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "product_type",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                }
            ],
            "parent_company": [
                {
                    "id": 986514,
                    "is_verified": false,
                    "value": {
                        "name": "Dekkoisho Group",
                        "raw_value": "Dekkoisho Group"
                    },
                    "updated_at": "2024-01-29T04:41:06.612658Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 2,
                    "is_from_claim": true,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6427760,
                    "is_verified": false,
                    "value": {
                        "name": "DEKKO GARMENTS LIMITED",
                        "raw_value": "DEKKO GARMENTS LIMITED"
                    },
                    "updated_at": "2026-05-20T17:46:55.671483Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3582802,
                    "is_verified": false,
                    "value": {
                        "name": "DEKKO GARMENTS LIMITED",
                        "raw_value": "DEKKO GARMENTS LIMITED"
                    },
                    "updated_at": "2025-05-23T16:37:31.653110Z",
                    "contributor_name": "a Brand / Retailer",
                    "contributor_id": null,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3048906,
                    "is_verified": false,
                    "value": {
                        "name": "Dekko Readywears Ltd",
                        "raw_value": "Dekko Readywears Ltd"
                    },
                    "updated_at": "2024-12-02T18:03:42.188989Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 730411,
                    "is_verified": false,
                    "value": {
                        "name": "Dekko Readywears Ltd",
                        "raw_value": "Dekko Readywears Ltd"
                    },
                    "updated_at": "2023-11-13T14:19:16.607435Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 393398,
                    "is_verified": false,
                    "value": {
                        "name": "DEKKO GARMENTS LIMITED",
                        "raw_value": "DEKKO GARMENTS LIMITED"
                    },
                    "updated_at": "2023-04-05T17:12:36.973871Z",
                    "contributor_name": "Ralph Lauren Corporation",
                    "contributor_id": 1342,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 244452,
                    "is_verified": false,
                    "value": {
                        "name": "Dekko Readywears Ltd",
                        "raw_value": "Dekko Readywears Ltd"
                    },
                    "updated_at": "2022-11-02T11:07:56.028758Z",
                    "contributor_name": "HEMA B.V.",
                    "contributor_id": 841,
                    "value_count": 3,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3752264,
                    "is_verified": false,
                    "value": {
                        "name": "DI International Pte. Ltd.",
                        "raw_value": "DI International Pte. Ltd."
                    },
                    "updated_at": "2025-07-01T03:24:17.541522Z",
                    "contributor_name": "Kontoor Brands, Inc. (KTB)",
                    "contributor_id": 3394,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3161617,
                    "is_verified": false,
                    "value": {
                        "name": "Dekko Isho",
                        "raw_value": "Dekko Isho"
                    },
                    "updated_at": "2025-04-01T12:44:27.408696Z",
                    "contributor_name": "VARNER AS",
                    "contributor_id": 12108,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3132307,
                    "is_verified": false,
                    "value": {
                        "name": "DI International Pte. Ltd.",
                        "raw_value": "DI International Pte. Ltd."
                    },
                    "updated_at": "2025-02-20T03:20:13.288748Z",
                    "contributor_name": "Kontoor Brands, Inc. (KTB)",
                    "contributor_id": 3394,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 3095491,
                    "is_verified": false,
                    "value": {
                        "name": "Dekko Isho",
                        "raw_value": "Dekko Isho"
                    },
                    "updated_at": "2025-01-23T03:00:20.215734Z",
                    "contributor_name": "VARNER AS",
                    "contributor_id": 12108,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1102127,
                    "is_verified": false,
                    "value": {
                        "name": "Globus Garments Ltd.",
                        "raw_value": "Globus Garments Ltd."
                    },
                    "updated_at": "2024-04-02T23:43:21.919533Z",
                    "contributor_name": "Tom Tailor GmbH",
                    "contributor_id": 1237,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 318715,
                    "is_verified": false,
                    "value": {
                        "name": "Dekkoisho Group",
                        "raw_value": "Dekkoisho Group"
                    },
                    "updated_at": "2023-01-20T00:22:49.175914Z",
                    "contributor_name": "Dekko Garments Ltd.",
                    "contributor_id": 4402,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6591,
                    "is_verified": false,
                    "value": {
                        "name": "Globus Garments Ltd.",
                        "raw_value": "Globus Garments Ltd."
                    },
                    "updated_at": "2022-04-28T21:13:39.309100Z",
                    "contributor_name": "Tom Tailor [Public List]",
                    "contributor_id": 913,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 6461689,
                    "is_verified": false,
                    "value": {
                        "raw_value": "Dekko Garments Ltd.",
                        "contributor_id": 4393,
                        "contributor_name": "Dekko Garments Ltd."
                    },
                    "updated_at": "2026-06-26T16:51:48.690163Z",
                    "contributor_name": "Levi Strauss & Co.",
                    "contributor_id": 26,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 4858927,
                    "is_verified": false,
                    "value": {
                        "name": "Dekko Isso",
                        "raw_value": "Dekko Isso"
                    },
                    "updated_at": "2025-12-03T18:23:10.172510Z",
                    "contributor_name": "VARNER AS",
                    "contributor_id": 12108,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 1959031,
                    "is_verified": false,
                    "value": {
                        "name": "Dekko ISHO Group",
                        "raw_value": "Dekko ISHO Group"
                    },
                    "updated_at": "2024-07-15T18:40:39.892494Z",
                    "contributor_name": "Dekko ISHO [Public List]",
                    "contributor_id": 6597,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                },
                {
                    "id": 372749,
                    "is_verified": false,
                    "value": {
                        "name": "Dekko Apparels Ltd.",
                        "raw_value": "Dekko Apparels Ltd."
                    },
                    "updated_at": "2023-03-31T14:49:41.320082Z",
                    "contributor_name": "Esprit",
                    "contributor_id": 3126,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "parent_company",
                    "verified_count": 0,
                    "source_by": null,
                    "unit": null,
                    "label": null,
                    "base_url": null,
                    "display_text": null,
                    "json_schema": null
                }
            ],
            "parent_company_os_id": [],
            "duns_id": [],
            "lei_id": [],
            "rba_id": [],
            "isic_4": []
        },
        "created_from": {
            "created_at": "2023-01-18T03:08:13.143688Z",
            "contributor": "Dekko Garments Ltd."
        },
        "sector": [
            {
                "updated_at": "2026-04-04T06:17:21.227785Z",
                "contributor_id": 4402,
                "contributor_name": "Dekko Garments Ltd.",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": true
            },
            {
                "updated_at": "2026-06-30T20:25:02.560500Z",
                "contributor_id": 4699,
                "contributor_name": "J.Crew Group",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-06-30T18:32:04.086915Z",
                "contributor_id": 2238,
                "contributor_name": "International Accord",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-06-26T16:51:30.071025Z",
                "contributor_id": 26,
                "contributor_name": "Levi Strauss & Co.",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-05-28T02:34:26.017209Z",
                "contributor_id": 2745,
                "contributor_name": "BESTSELLER",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-05-27T17:38:58.573347Z",
                "contributor_id": 6294,
                "contributor_name": "PVH",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-05-20T17:46:35.171352Z",
                "contributor_id": 1342,
                "contributor_name": "Ralph Lauren Corporation",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-01-27T13:40:16.579843Z",
                "contributor_id": 19188,
                "contributor_name": "Helly Hansen",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2025-12-03T18:22:54.757473Z",
                "contributor_id": 12108,
                "contributor_name": "VARNER AS",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2025-12-03T17:48:36.347207Z",
                "contributor_id": 6563,
                "contributor_name": "Sainsbury's",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2025-10-30T09:46:04.823793Z",
                "contributor_id": 17853,
                "contributor_name": "Bangladesh Department of Inspection for Factories and Establishments (LIMA) [Public List]",
                "values": [
                    "Apparel",
                    "Textiles"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2025-08-18T16:23:52.768378Z",
                "contributor_id": null,
                "contributor_name": "a Civil Society Organization",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2025-07-01T03:24:01.998936Z",
                "contributor_id": 3394,
                "contributor_name": "Kontoor Brands, Inc. (KTB)",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2025-06-24T23:52:05.083072Z",
                "contributor_id": 205,
                "contributor_name": "Mapped in Bangladesh (MiB) - BRAC University",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-12-02T18:03:17.252409Z",
                "contributor_id": 841,
                "contributor_name": "HEMA B.V.",
                "values": [
                    "Textiles"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-10-07T23:20:39.493683Z",
                "contributor_id": null,
                "contributor_name": "a Civil Society Organization",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-07-15T18:40:39.813671Z",
                "contributor_id": 6597,
                "contributor_name": "Dekko ISHO [Public List]",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-05-01T16:28:25.478381Z",
                "contributor_id": null,
                "contributor_name": "a Brand / Retailer",
                "values": [
                    "Apparel",
                    "Textiles"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-04-29T16:48:34.573950Z",
                "contributor_id": null,
                "contributor_name": "a Brand / Retailer",
                "values": [
                    "Multi-Category"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-04-02T23:43:20.272385Z",
                "contributor_id": 1237,
                "contributor_name": "Tom Tailor GmbH",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2023-09-05T07:02:47.837612Z",
                "contributor_id": null,
                "contributor_name": "a Multi-Stakeholder Initiative",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2023-03-31T14:49:13.526431Z",
                "contributor_id": 3126,
                "contributor_name": "Esprit",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2022-10-28T01:26:24.151562Z",
                "contributor_id": null,
                "contributor_name": "a Multi-Stakeholder Initiative",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2022-10-25T16:16:45.014936Z",
                "contributor_id": 3757,
                "contributor_name": "Bangladesh Industrial Import Registration Certificate (IRC) [Public List]",
                "values": [
                    "Apparel",
                    "Government Registry"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2022-10-23T18:16:19.520220Z",
                "contributor_id": 97,
                "contributor_name": "Fair Factories Clearinghouse",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2022-09-06T05:59:29.765465Z",
                "contributor_id": null,
                "contributor_name": "an Auditor / Certification Scheme / Service Provider",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2022-01-27T17:41:06.088215Z",
                "contributor_id": 5102,
                "contributor_name": "Better Cotton",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2022-01-27T17:37:57.363483Z",
                "contributor_id": null,
                "contributor_name": "a Brand / Retailer",
                "values": [
                    "Apparel"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-06-25T19:20:59.918310Z",
                "contributor_id": 8742,
                "contributor_name": "Target Corporation",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-06-03T10:34:54.776576Z",
                "contributor_id": 3365,
                "contributor_name": "amfori",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-05-14T20:54:17.597126Z",
                "contributor_id": 2144,
                "contributor_name": "Nirapon Inc.",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-04-23T18:51:24.893903Z",
                "contributor_id": 11889,
                "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-04-18T02:03:56.109833Z",
                "contributor_id": 20593,
                "contributor_name": "Climate TRACE",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-04-17T06:35:34.603332Z",
                "contributor_id": 13389,
                "contributor_name": "Social & Labor Convergence Program (SLCP)",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-03-26T03:25:19.398318Z",
                "contributor_id": 1673,
                "contributor_name": "KIABI",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2026-01-07T08:09:24.627717Z",
                "contributor_id": 12266,
                "contributor_name": "Tesco Stores Ltd",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2025-08-08T17:20:33.180902Z",
                "contributor_id": 11651,
                "contributor_name": "Wm Morrison Supermarkets Limited",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-05-25T10:15:11.808687Z",
                "contributor_id": 686,
                "contributor_name": "Worldly",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-03-27T01:14:50.822943Z",
                "contributor_id": 1050,
                "contributor_name": "ZDHC Foundation",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2024-01-26T19:30:12.772054Z",
                "contributor_id": 7745,
                "contributor_name": "RISE",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2023-04-25T12:22:40.641970Z",
                "contributor_id": null,
                "contributor_name": "a Multi-Stakeholder Initiative",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            },
            {
                "updated_at": "2023-01-22T14:39:15.048576Z",
                "contributor_id": 4402,
                "contributor_name": "Dekko Garments Ltd.",
                "values": [
                    "Unspecified"
                ],
                "is_from_claim": false
            }
        ],
        "is_claimed": true,
        "partner_fields": {
            "rsc_grievance_mechanism": [
                {
                    "id": 6385810,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "status": "Active",
                            "internal_ID": "9214"
                        }
                    },
                    "updated_at": "2026-04-17T04:05:25.861110Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "rsc_grievance_mechanism",
                    "verified_count": 0,
                    "source_by": "<p>Mechanism Active in Bangladesh Since August 1, 2014</p>",
                    "unit": "",
                    "label": "Accord/RSC Grievance Mechanism",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "type": "object",
                        "title": "RSC Grievance Mechanism",
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "required": [
                            "status"
                        ],
                        "properties": {
                            "status": {
                                "enum": [
                                    "Active",
                                    "Inactive"
                                ],
                                "type": "string",
                                "title": "Status",
                                "description": "The current operational status."
                            },
                            "thematic_coverage": {
                                "type": "string",
                                "title": "Thematic Coverage",
                                "default": "Multi-issue"
                            },
                            "mechanism_type_ownership": {
                                "type": "string",
                                "title": "Mechanism Type / Ownership",
                                "default": "Multi-stakeholder led"
                            },
                            "access_modality": {
                                "type": "string",
                                "title": "Access / Modality",
                                "default": "Hotline; Email; In-person"
                            },
                            "coverage": {
                                "type": "string",
                                "title": "Coverage",
                                "default": "All workers (factory-level)"
                            }
                        }
                    }
                }
            ],
            "wrap_certification": [
                {
                    "id": 6404862,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "issue_date": "2025-05-12",
                            "expiration_date": "2026-05-12",
                            "certification_status": "active"
                        }
                    },
                    "updated_at": "2026-04-23T18:51:24.974544Z",
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "contributor_id": 11889,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "wrap_certification",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "WRAP Certification",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "title": "WRAP Certification",
                        "type": "object",
                        "properties": {
                            "certification_status": {
                                "type": "string",
                                "description": "The current certification status.",
                                "title": "Status",
                                "enum": [
                                    "active",
                                    "inactive"
                                ]
                            },
                            "issue_date": {
                                "type": "string",
                                "format": "date",
                                "title": "Issue Date",
                                "description": "The date the certification was issued."
                            },
                            "expiration_date": {
                                "type": "string",
                                "format": "date",
                                "title": "Expiration Date",
                                "description": "The date the certification expires."
                            }
                        },
                        "required": [
                            "certification_status"
                        ]
                    }
                },
                {
                    "id": 6403708,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "issue_date": "2025-05-12",
                            "expiration_date": "2026-05-12",
                            "certification_status": "active"
                        }
                    },
                    "updated_at": "2026-04-23T17:13:44.877308Z",
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "contributor_id": 11889,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "wrap_certification",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "WRAP Certification",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "title": "WRAP Certification",
                        "type": "object",
                        "properties": {
                            "certification_status": {
                                "type": "string",
                                "description": "The current certification status.",
                                "title": "Status",
                                "enum": [
                                    "active",
                                    "inactive"
                                ]
                            },
                            "issue_date": {
                                "type": "string",
                                "format": "date",
                                "title": "Issue Date",
                                "description": "The date the certification was issued."
                            },
                            "expiration_date": {
                                "type": "string",
                                "format": "date",
                                "title": "Expiration Date",
                                "description": "The date the certification expires."
                            }
                        },
                        "required": [
                            "certification_status"
                        ]
                    }
                },
                {
                    "id": 6401192,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "issue_date": "2025-05-12",
                            "expiration_date": "2026-05-12",
                            "certification_status": "active"
                        }
                    },
                    "updated_at": "2026-04-22T14:14:23.315180Z",
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "contributor_id": 11889,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "wrap_certification",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "WRAP Certification",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "title": "WRAP Certification",
                        "type": "object",
                        "properties": {
                            "certification_status": {
                                "type": "string",
                                "description": "The current certification status.",
                                "title": "Status",
                                "enum": [
                                    "active",
                                    "inactive"
                                ]
                            },
                            "issue_date": {
                                "type": "string",
                                "format": "date",
                                "title": "Issue Date",
                                "description": "The date the certification was issued."
                            },
                            "expiration_date": {
                                "type": "string",
                                "format": "date",
                                "title": "Expiration Date",
                                "description": "The date the certification expires."
                            }
                        },
                        "required": [
                            "certification_status"
                        ]
                    }
                },
                {
                    "id": 6396790,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "issue_date": "2025-05-12",
                            "expiration_date": "2026-05-12",
                            "certification_status": "active"
                        }
                    },
                    "updated_at": "2026-04-17T20:04:06.208994Z",
                    "contributor_name": "Worldwide Responsible Accredited Production (WRAP)",
                    "contributor_id": 11889,
                    "value_count": 4,
                    "is_from_claim": false,
                    "field_name": "wrap_certification",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "WRAP Certification",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "title": "WRAP Certification",
                        "type": "object",
                        "properties": {
                            "certification_status": {
                                "type": "string",
                                "description": "The current certification status.",
                                "title": "Status",
                                "enum": [
                                    "active",
                                    "inactive"
                                ]
                            },
                            "issue_date": {
                                "type": "string",
                                "format": "date",
                                "title": "Issue Date",
                                "description": "The date the certification was issued."
                            },
                            "expiration_date": {
                                "type": "string",
                                "format": "date",
                                "title": "Expiration Date",
                                "description": "The date the certification expires."
                            }
                        },
                        "required": [
                            "certification_status"
                        ]
                    }
                }
            ],
            "accord_inspections_and_remediation_program": [
                {
                    "id": 6344347,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "rsc_presence": "Yes",
                            "first_inspection_date": "2019-04-08"
                        }
                    },
                    "updated_at": "2026-04-03T04:44:09.644543Z",
                    "contributor_name": "International Accord",
                    "contributor_id": 2238,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "accord_inspections_and_remediation_program",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "Accord Inspections & Remediation Program",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "type": "object",
                        "title": "Accord Inspections and Remediation Program",
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "properties": {
                            "rsc_presence": {
                                "enum": [
                                    "Yes",
                                    "No"
                                ],
                                "type": "string",
                                "title": "Accord/RSC Presence"
                            },
                            "first_inspection_date": {
                                "type": "string",
                                "title": "First Inspection Date",
                                "format": "date"
                            }
                        }
                    }
                }
            ],
            "slcp_assessment": [
                {
                    "id": 6388213,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "verifier_body": "N/A - Better Work Bangladesh (not a Verifier Body)",
                            "slcp_facility_id": "FA500170",
                            "assessment_platform": "N/A - Data shared by Better Work",
                            "most_recent_assessment_date": "2026-03-30",
                            "most_recent_assessment_status": "Assessment Initiated"
                        }
                    },
                    "updated_at": "2026-04-17T06:35:34.676361Z",
                    "contributor_name": "Social & Labor Convergence Program (SLCP)",
                    "contributor_id": 13389,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "slcp_assessment",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "SLCP Assessment",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "type": "object",
                        "title": "SLCP Assessment",
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "properties": {
                            "most_recent_assessment_status": {
                                "enum": [
                                    "Assessment Initiated",
                                    "Assessment Completed",
                                    "Assessment Deleted",
                                    "Verification in Progress",
                                    "Verification Quality Check",
                                    "Verification Being Edited",
                                    "Verification Completed",
                                    "Verification Disputed",
                                    "Verification Finalized",
                                    "Verification Invalidated"
                                ],
                                "type": "string",
                                "title": "Assessment Status",
                                "description": "The verification status of the most recent CAF assessment."
                            },
                            "most_recent_assessment_date": {
                                "type": "string",
                                "title": "Assessment Date",
                                "format": "date",
                                "description": "The date of the most recent CAF assessment."
                            },
                            "assessment_platform": {
                                "type": "string",
                                "title": "Assessment Platform",
                                "description": "The platform used to conduct the CAF assessment."
                            },
                            "verifier_body": {
                                "type": "string",
                                "title": "Verifier Body",
                                "description": "The organization that verified the CAF assessment."
                            },
                            "slcp_facility_id": {
                                "type": "string",
                                "title": "SLCP Facility ID",
                                "description": "The unique facility identifier assigned by SLCP (e.g., FA1000010)."
                            }
                        }
                    }
                },
                {
                    "id": 6374703,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "verifier_body": "PDCA International Ltd.",
                            "slcp_facility_id": "FA500170",
                            "assessment_platform": "Worldly (FFC)",
                            "most_recent_assessment_date": "2025-04-10",
                            "most_recent_assessment_status": "Verification Finalized"
                        }
                    },
                    "updated_at": "2026-04-16T10:11:40.514628Z",
                    "contributor_name": "Social & Labor Convergence Program (SLCP)",
                    "contributor_id": 13389,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "slcp_assessment",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "SLCP Assessment",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "type": "object",
                        "title": "SLCP Assessment",
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "properties": {
                            "most_recent_assessment_status": {
                                "enum": [
                                    "Assessment Initiated",
                                    "Assessment Completed",
                                    "Assessment Deleted",
                                    "Verification in Progress",
                                    "Verification Quality Check",
                                    "Verification Being Edited",
                                    "Verification Completed",
                                    "Verification Disputed",
                                    "Verification Finalized",
                                    "Verification Invalidated"
                                ],
                                "type": "string",
                                "title": "Assessment Status",
                                "description": "The verification status of the most recent CAF assessment."
                            },
                            "most_recent_assessment_date": {
                                "type": "string",
                                "title": "Assessment Date",
                                "format": "date",
                                "description": "The date of the most recent CAF assessment."
                            },
                            "assessment_platform": {
                                "type": "string",
                                "title": "Assessment Platform",
                                "description": "The platform used to conduct the CAF assessment."
                            },
                            "verifier_body": {
                                "type": "string",
                                "title": "Verifier Body",
                                "description": "The organization that verified the CAF assessment."
                            },
                            "slcp_facility_id": {
                                "type": "string",
                                "title": "SLCP Facility ID",
                                "description": "The unique facility identifier assigned by SLCP (e.g., FA1000010)."
                            }
                        }
                    }
                }
            ],
            "amfori_compliance_status": [
                {
                    "id": 6458770,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "bsci_audit": {
                                "expiration_date": "2026-11-21",
                                "submission_date": "2024-11-21"
                            },
                            "environmental_risk_assessment": {
                                "completion_date": "2026-01-22"
                            }
                        }
                    },
                    "updated_at": "2026-06-03T10:34:54.858682Z",
                    "contributor_name": "amfori",
                    "contributor_id": 3365,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "amfori_compliance_status",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "amfori Assessment & Audits",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "type": "object",
                        "title": "Amfori Compliance Status",
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "properties": {
                            "bsci_audit": {
                                "type": "object",
                                "properties": {
                                    "expiration_date": {
                                        "type": "string",
                                        "title": "Expiration Date",
                                        "format": "date"
                                    },
                                    "submission_date": {
                                        "type": "string",
                                        "title": "Submission Date",
                                        "format": "date"
                                    }
                                }
                            },
                            "bepi_audit": {
                                "type": "object",
                                "properties": {
                                    "expiration_date": {
                                        "type": "string",
                                        "title": "Expiration Date",
                                        "format": "date"
                                    },
                                    "submission_date": {
                                        "type": "string",
                                        "title": "Submission Date",
                                        "format": "date"
                                    }
                                }
                            },
                            "environmental_risk_assessment": {
                                "type": "object",
                                "properties": {
                                    "completion_date": {
                                        "type": "string",
                                        "title": "Completion Date",
                                        "format": "date"
                                    },
                                    "expiration_date": {
                                        "type": "string",
                                        "title": "Expiration Date",
                                        "format": "date"
                                    }
                                }
                            }
                        }
                    }
                },
                {
                    "id": 6348449,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "bepi_audit": {
                                "expiration_date": "2025-05-04",
                                "submission_date": "2023-05-04"
                            },
                            "bsci_audit": {
                                "expiration_date": "2026-11-21",
                                "submission_date": "2024-11-21"
                            },
                            "environmental_risk_assessment": {
                                "completion_date": "2026-01-22"
                            }
                        }
                    },
                    "updated_at": "2026-04-08T09:12:11.110604Z",
                    "contributor_name": "amfori",
                    "contributor_id": 3365,
                    "value_count": 1,
                    "is_from_claim": false,
                    "field_name": "amfori_compliance_status",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "amfori Assessment & Audits",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "type": "object",
                        "title": "Amfori Compliance Status",
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "properties": {
                            "bsci_audit": {
                                "type": "object",
                                "properties": {
                                    "expiration_date": {
                                        "type": "string",
                                        "title": "Expiration Date",
                                        "format": "date"
                                    },
                                    "submission_date": {
                                        "type": "string",
                                        "title": "Submission Date",
                                        "format": "date"
                                    }
                                }
                            },
                            "bepi_audit": {
                                "type": "object",
                                "properties": {
                                    "expiration_date": {
                                        "type": "string",
                                        "title": "Expiration Date",
                                        "format": "date"
                                    },
                                    "submission_date": {
                                        "type": "string",
                                        "title": "Submission Date",
                                        "format": "date"
                                    }
                                }
                            },
                            "environmental_risk_assessment": {
                                "type": "object",
                                "properties": {
                                    "completion_date": {
                                        "type": "string",
                                        "title": "Completion Date",
                                        "format": "date"
                                    },
                                    "expiration_date": {
                                        "type": "string",
                                        "title": "Expiration Date",
                                        "format": "date"
                                    }
                                }
                            }
                        }
                    }
                }
            ],
            "climate_trace_emissions": [
                {
                    "id": 6398744,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "emissions_model": "Fully Modeled",
                            "estimated_emissions": 546
                        }
                    },
                    "updated_at": "2026-04-18T02:03:56.182755Z",
                    "contributor_name": "Climate TRACE",
                    "contributor_id": 20593,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "climate_trace_emissions",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "Climate TRACE Emissions",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "type": "object",
                        "title": "Climate TRACE Estimated Emissions",
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "properties": {
                            "estimated_emissions": {
                                "type": "integer",
                                "title": "Estimated Annual Emissions (t CO₂e-100)",
                                "description": "Total CO₂e using 100-year GWP, measured in metric tons (t CO₂e-100)"
                            },
                            "estimated_annual_throughput": {
                                "type": "integer",
                                "title": "Estimated Annual Throughput (kg/yr)",
                                "description": "Estimated annual production throughput in tonnes per year. Populated when the facility provides feasible throughput data or when throughput can be calculated from fuel consumption. Left blank when neither throughput nor fuel consumption data is provided."
                            },
                            "emissions_model": {
                                "type": "string",
                                "title": "Emissions Model",
                                "enum": [
                                    "Facility Reported",
                                    "Partially Reported",
                                    "Partially Modeled",
                                    "Fully Modeled"
                                ],
                                "description": "Methodology used by Climate TRACE to calculate emissions, indicating the hierarchy of data quality from best (Facility Reported) to lowest (Fully Modeled)."
                            }
                        },
                        "required": [
                            "estimated_emissions",
                            "emissions_model"
                        ]
                    }
                },
                {
                    "id": 6398696,
                    "is_verified": false,
                    "value": {
                        "raw_values": {
                            "emissions_model": "Fully Modeled",
                            "estimated_emissions": 546
                        }
                    },
                    "updated_at": "2026-04-18T01:03:55.345022Z",
                    "contributor_name": "Climate TRACE",
                    "contributor_id": 20593,
                    "value_count": 2,
                    "is_from_claim": false,
                    "field_name": "climate_trace_emissions",
                    "verified_count": 0,
                    "source_by": "",
                    "unit": "",
                    "label": "Climate TRACE Emissions",
                    "base_url": "",
                    "display_text": "",
                    "json_schema": {
                        "type": "object",
                        "title": "Climate TRACE Estimated Emissions",
                        "$schema": "https://json-schema.org/draft/2020-12/schema",
                        "properties": {
                            "estimated_emissions": {
                                "type": "integer",
                                "title": "Estimated Annual Emissions (t CO₂e-100)",
                                "description": "Total CO₂e using 100-year GWP, measured in metric tons (t CO₂e-100)"
                            },
                            "estimated_annual_throughput": {
                                "type": "integer",
                                "title": "Estimated Annual Throughput (kg/yr)",
                                "description": "Estimated annual production throughput in tonnes per year. Populated when the facility provides feasible throughput data or when throughput can be calculated from fuel consumption. Left blank when neither throughput nor fuel consumption data is provided."
                            },
                            "emissions_model": {
                                "type": "string",
                                "title": "Emissions Model",
                                "enum": [
                                    "Facility Reported",
                                    "Partially Reported",
                                    "Partially Modeled",
                                    "Fully Modeled"
                                ],
                                "description": "Methodology used by Climate TRACE to calculate emissions, indicating the hierarchy of data quality from best (Facility Reported) to lowest (Fully Modeled)."
                            }
                        },
                        "required": [
                            "estimated_emissions",
                            "emissions_model"
                        ]
                    }
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
