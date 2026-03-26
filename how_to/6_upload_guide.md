# How to Upload Data via API

Learn how to submit data to OS Hub and automatically match against existing production locations in the database.

## Overview

The POST /facilities/ endpoint allows you to upload data to OS Hub. When you submit facility information, the API automatically searches for existing matches in the database. By default:

- **No match found**: A new production location (OS ID) is created
- **Confident match found**: Your contribution is added to an existing production location

## Endpoint

```
POST https://opensupplyhub.org/api/facilities/
```

## Query Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `create` | Boolean | `true` | When set to `false`, prevents creation of a new facility if no match is found |
| `public` | Boolean | `true` | For anonymized contribution. When set to `false`, attributes the contribution to contributor type (e.g. "A Brand/Retailer", "A Civil Society Organization" instead of contributor name. *Only available with certain API packages* |

## Request Body

All requests must be submitted in JSON format with the following structure:

### Required Fields

| Field | Type | Description |
|-------|------|-------------|
| `name` | String | Name of the facility |
| `address` | String | Street address (excluding country). Must include street number, street name, city and zip/postal code.|
| `country` | String | Country where the facility is located |

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `product_type` | String | Product type produced or processed at the facility. Can also be included in `sector_product_type` |
| `sector` | String | Industry sector associated with the facility. Can also be included in `sector_product_type` |
| `sector_product_type` | String | Combined field for product types and/or sectors. Values matching the [OS Hub sector list](https://docs.google.com/document/d/12gDb4WlMHwaAE0iYVmbOjNJ_T7ICqntp-Ddd1qfbhCg/edit?tab=t.0#heading=h.tnf5hn3volep) appear as sectors; others appear as product types |
| `facility_type` | String | Type of facility (e.g., "Final Product Assembly"). See [OS Hub taxonomy](https://docs.google.com/spreadsheets/d/18ABJuS5CY4cr9JaTzPeLaAr1uhdu7VJXK6JpibP1b1o/edit?gid=0#gid=0) |
| `processing_type` | String | Processing activity type (e.g., "printing"). Matching types from the [OS Hub taxonomy](https://docs.google.com/spreadsheets/d/18ABJuS5CY4cr9JaTzPeLaAr1uhdu7VJXK6JpibP1b1o/edit?gid=0#gid=0)) automatically add the associated facility type |
| `facility_type_processing_type` | String | Combined field for facility type and processing type. Matching processing types automatically add associated facility types |
| `parent_company` | String | Company with majority ownership of the facility |
| `number_of_workers` | Integer or String | Number or range of workers (e.g., `"100"` or `"100-150"`) |

## Examples

To see example request body and response, visit the [API Endpoints Reference](https://opensupplyhub.org/api/docs/)

## Response

The API processes your submission through OS Hub's matching algorithm and returns one of three possible outcomes:

### Automatic Match

**Occurs when**: A single existing facility is found with >0.8 confidence score

The system automatically adds your contribution to the existing facility record. The response includes:
- OS ID of the matched facility
- Match confidence score (>0.8)
- Facility details as stored in OS Hub
- Confirmation that data was added to existing record

### Potential Match

**Occurs when**: 
- One or more existing facilities are found with 0.5-0.8 confidence, OR
- Multiple existing facilities are found with >0.8 confidence

The response includes:
- List of potential matching facilities
- Confidence scores for each potential match
- `confirm_match_url` - URL to confirm a match
- `reject_match_url` - URL to reject a match

**Required action**: You must respond to the API using the provided URLs to either:
- **Confirm a match**: POST to the `confirm_match_url` to add your data to the selected facility
- **Reject all matches**: POST to the `reject_match_url` for each potential match. Once all are rejected, the system creates a new facility

### New Facility

**Occurs when**: No existing facilities are found with ≥0.5 confidence score

The system creates a new facility record. The response includes:
- Newly assigned OS ID
- Complete facility details as submitted
- Confirmation of new facility creation

## Best Practices

1. **Use consistent naming**: Provide the complete legal name of the production location, include incorporation details (Pvt., Ltd., etc.)
2. **Include complete addresses**: More detailed addresses improve matching confidence and geocoding accuracy
3. **Leverage optional fields**: Additional context improves the overall data quality
4. **Test matching behavior**: Use `create=false` to test matching without creating new facilities
5.  **Convert all text to English/Roman language**: to ensure the data is searchable, translate any non-roman characters to Roman / English equivalent
