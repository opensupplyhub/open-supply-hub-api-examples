## Rate Limits

### Daily Call Limits

API user accounts have default settings limiting the number of calls allowed per minute and day.

| Rate Type | Limit | Details |
|-----------|-------|---------|
| **Burst Rate** | 100 calls/minute | Most endpoints (144k per day) |
| **Sustained Rate** | 10,000 calls/day | Excluding POST calls to facilities endpoint |
| **Data Upload Rate** | 30 calls/minute | POST calls to facilities endpoint (43.2k per day) |

---

## Endpoints

### `GET /api/facilities/`

The facilities endpoint returns a maximum number of facilities per page based on the `detail` parameter.

#### Response Limits

| Parameter | Facilities Per Page | Use Case |
|-----------|-------------------|----------|
| Default (no parameters) | 50 | Standard requests |
| `detail=false` or not specified | 50 | Basic facility data |
| `detail=true` | 10 | Detailed facility information |

#### Managing Large Data Requests

- Use the `page` and `pageSize` parameters to navigate through large datasets efficiently
- **Maximum page limit: 100 pages**
- For datasets requiring more than 100 pages consider using a [data download](https://info.opensupplyhub.org/premium-data-downloads-analysis) instead.

> ⚠️ **Important**: The page limit of 100 is enforced to ensure system stability and prevent excessive load on the OS Hub platform.

#### Error Handling

If you set the `page` parameter higher than 100, the request will return an error message (see example screnshot below).

<img width="1932" height="950" alt="image" src="https://github.com/user-attachments/assets/7c12a0e0-67cb-4f65-b91f-2c1405146f68" />
---

## GPS Coordinates Upload

### Legacy Endpoint: `POST /api/facilities/`

> ⚠️ **Known Issue**: This endpoint accepts GPS coordinates but does not process them. It automatically performs geocoding based on the provided address, ignoring any coordinates in the request.

**Workaround:**
- Upload data using an Excel spreadsheet. [Reach out to our team](https://info.opensupplyhub.org/contact-us) for a custom template to include GPS coordinates in your upload.

### New Endpoint: `POST /api/v1/production-locations/` (Future solution, still in Beta)

✅ **Recommended**: This endpoint correctly accepts and processes GPS coordinates.

- Once the moderation event for the new location is approved, coordinates will appear on the location profile page
- For immediate GPS coordinate uploads, use the list upload method or switch to this new endpoint once available outside of beta

---

## API Health Check

### Current Status Monitoring

OS Hub does not currently have a dedicated health check API endpoint.

#### Recommended Method

Query the health check URL to verify platform availability:

```
GET https://opensupplyhub.org/health-check/
```

**Benefits:**
- ✅ No authentication required
- ✅ Does not count against API call limits
- ✅ Confirms general platform availability

> ⚠️ **Note**: This check confirms platform availability but does not represent the status of all API functionalities.

#### Future Development

A dedicated API health check endpoint is planned but not currently in development.
