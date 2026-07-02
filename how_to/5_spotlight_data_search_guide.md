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

### Response structure for the GET /api/facilities/{id} endpoint

> **Note:** The example below is a real production location on OS Hub, so not all fields will be populated. For the complete schema including all possible fields, see the [Endpoint reference documentation](https://opensupplyhub.org/api/docs/).


<details>
<summary>Example response for OS ID <code>BD2020021QK28YZ</code></summary>


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
            "DEKKO GARMENTS LTD.",
            "DEKKO GARMENTS LTD",
            "DEKKO GARMENTS LIMITED",
            "Dekko Garments Limited",
            "Dekko Garments Ltd"
        ],
        "other_addresses": [
            "Nayanpur, Mawna, Sreepur",
            "Mawna, Sreepur, Gazipur, Gazipur, Gazipur, 1740",
            "Nayanpur, Mawna, Sreepur, 1703, Gazipur",
            "Mawna, Sreepur, Gazipur. Bangladesh",
            "Nayanpur, Mawna, Sreepur, 1740 Gazipur, Bangladesh",
            "Mawna, Sreepur,Dhaka Gazipur",
            "Mawna,Sreepur,, Gazipur.",
            "Nayanpur, Mawna, Sreepur BD, GAZIPUR SADAR, Bangladesh",
            "Mawna, Sreepur, Gazipur.",
            "Mawna - Sreepur Rd, Sreepur, Bangladesh",
            "Noyanpur Bazar Road, Mawna Union, Bangladesh",
            "Mawna, Sreepur, Gazipur",
            "Nayanpur, Mawna, Sreepur, Gazipur.",
            "Nayanpur, Mawna, Sreepur, Gazipur., Gazipur",
            "Mawna, Sreepur, Gazipur, Gazipur, Gazipur 1740",
            "MAWNA, SREEPUR, GAZIPUR, MAWNA UTTARPARA, GAZIPUR, DHAKA",
            "Mawna, Sreepur, Dhaka Gazipur 1703",
            "MAWNA, SREEPUR,, GAZIPUR, Dhaka 1740",
            "Mawna, Sreepur, Gazipur   ",
            "Mawna, Sreepur, Gazipur, Nayanpur, Sreepur, Gazipur, GazipurBangladesh",
            "Mawna, Sreepur, Gazipur-1740",
            "Mawna, Sreepur, Gazipur - 1740, Bangladesh",
            "Mawna, Sreepur, 1740, Gazipur",
            "Nayanpur, Mawna, Sreepur, Gazipur, Mawna Uttarpara, Gazipur 1703, Dhaka",
            "Mawna, Sreepur, Gazipur, Dhaka",
            "Mawna, Sreepur",
            "Mawna, 1740, Sreepur, Gazipur, Gazipur",
            "MAWNA, SREEPUR, GAZIPUR,MAWNA UTTARPARA,,GAZIPUR, DHAKA,BANGLADESH",
            "Mawna, Sreepur, Gazipur, Dhaka, Bangladesh",
            "MAWNA, SREEPUR, GAZIPUR, Dhaka",
            "Mawna, Sreepur, Gazipur-1740.",
            "(Ground Floor), Dekko Garments Road, Nayanpur, Sreepur, Gazipur-1740",
            "Dekko Garments Ltd, Mawna, Sreepur\nDhaka zila\nGazipur\n1740"
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
                "id": 1673,
                "name": "KIABI (Kiabi June 23, 2026)",
                "is_verified": false,
                "contributor_name": "KIABI",
                "contributor_type": "Brand / Retailer",
                "list_name": "Kiabi June 23, 2026",
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
            }
        ],
        "is_closed": null,
        "activity_reports": [],
        "contributor_fields": [],
        "new_os_id": null,
        "has_inexact_coordinates": false,
        "extended_fields": {
            "name": ["... see full schema in endpoint reference ..."],
            "address": ["... see full schema in endpoint reference ..."],
            "number_of_workers": ["... see full schema in endpoint reference ..."],
            "native_language_name": ["... see full schema in endpoint reference ..."],
            "facility_type": ["... see full schema in endpoint reference ..."],
            "processing_type": ["... see full schema in endpoint reference ..."],
            "product_type": ["... see full schema in endpoint reference ..."],
            "parent_company": ["... see full schema in endpoint reference ..."],
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
        "sector": ["... see full schema in endpoint reference ..."],
        "is_claimed": true,
        "partner_fields": {
            "rsc_grievance_mechanism": ["... see full schema in endpoint reference ..."],
            "wrap_certification": ["... see full schema in endpoint reference ..."],
            "accord_inspections_and_remediation_program": ["... see full schema in endpoint reference ..."],
            "slcp_assessment": ["... see full schema in endpoint reference ..."],
            "amfori_compliance_status": ["... see full schema in endpoint reference ..."],
            "climate_trace_emissions": ["... see full schema in endpoint reference ..."]
        }
    }
}
```

</details>

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

### Response structure for the GET /api/v1/production-locations/{os_id} endpoint

> **Note:** The example below is a real production location on OS Hub, so not all fields will be populated. For the complete schema including all possible fields, see the [Endpoint reference documentation](https://opensupplyhub.github.io/open-supply-hub-api-docs/).

<details>
<summary>Example response for OS ID <code>BD2020021QK28YZ</code></summary>

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

</details>

## Frequently Asked Questions

**Will every production location have partner data?**

No. Partner data is only present when a partner has contributed information for that specific location. Most production locations will only contain a subset of partner data fields, so responses will vary.

**Can I retrieve partner data when searching across multiple production locations?**

No. Partner data is only returned when retrieving a specific production location by OS ID. It is not included in list responses, such as filtered searches by country, sector, or other parameters.

**How many API calls are needed to retrieve partner data for a production location?**

One. Partner data is included in the same response as the core production location data, so a single call per OS ID is all that is required.
