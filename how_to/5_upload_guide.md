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
| `public` | Boolean | `true` | When set to `false`, attributes the contribution to contributor type instead of contributor name. *Only available with certain API packages* |

## Request Body

All requests must be submitted in JSON format with the following structure:

### Required Fields

| Field | Type | Description |
|-------|------|-------------|
| `name` | String | Name of the facility |
| `address` | String | Street address (excluding country) |
| `country` | String | Country where the facility is located |

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `product_type` | String | Product type produced or processed at the facility. Can also be included in `sector_product_type` |
| `sector` | String | Industry sector associated with the facility. Can also be included in `sector_product_type` |
| `sector_product_type` | String | Combined field for product types and/or sectors. Values matching the [OS Hub sector list](https://opensupplyhub.org/sectors) appear as sectors; others appear as product types |
| `facility_type` | String | Type of facility (e.g., "Final Product Assembly"). See [OS Hub taxonomy](https://info.opensupplyhub.org/resources/facilitate-types) |
| `processing_type` | String | Processing activity type (e.g., "printing"). Matching types from the [OS Hub taxonomy](https://info.opensupplyhub.org/resources/processing-types) automatically add the associated facility type |
| `facility_type_processing_type` | String | Combined field for facility type and processing type. Matching processing types automatically add associated facility types |
| `parent_company` | String | Company with majority ownership of the facility |
| `number_of_workers` | Integer or String | Number or range of workers (e.g., `"100"` or `"100-150"`) |

## Response

The API returns details about the matched or created facility, including:

- OS ID (unique facility identifier)
- Match confidence score
- Whether a new facility was created or an existing one was matched
- Facility details as stored in OS Hub

## Best Practices

1. **Use consistent naming**: Submit facility names consistently to improve match accuracy
2. **Include complete addresses**: More detailed addresses improve matching confidence
3. **Leverage optional fields**: Additional context helps with data quality
4. **Test matching behavior**: Use `create=false` to test matching without creating new facilities
5. **Handle responses**: Check match confidence scores to understand how your data was processed
