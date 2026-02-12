# OS Hub API Quick Start Guide

Get up and running with the OS Hub API in minutes. This guide walks you through everything you need to make your first API request.

---

## Before You Begin

**Prerequisites:**
- An OS Hub account
- An active API subscription or trial
- Basic knowledge of REST APIs and HTTP requests
- A tool for making API requests (e.g., cURL, Postman, or your preferred programming language)

> **💡 Tip:** New to APIs? Check out these resources:
> - [GitHub: Working with REST APIs](https://docs.github.com/en/rest/guides/getting-started-with-the-rest-api)
> - [Mozilla: HTTP Guide](https://developer.mozilla.org/en-US/docs/Web/HTTP)

---

## Step 1: Get API Access

To access the OS Hub API, you'll need an active subscription or trial.

**Getting started:**
1. Visit [Connect to OS Hub's API](https://info.opensupplyhub.org/api) to purchase a subscription package
2. Choose the package that fits your needs and start your subscription
3. We will contact you within 2 business day with instructions to obtain your API Token

**How to check if you already have access:**
1. Log into [OS Hub](https://opensupplyhub.org)
2. Navigate to **My Account > Settings**
3. Look for an **API** tab in the settings menu

> **⚠️ Note:** If you don't see an "API" tab, you don't have API access yet. Contact [support](support@opensupplyhub.org) or complete your subscription.

---

## Step 2: Generate Your API Token

Your API token authenticates all requests to the OS Hub API. Keep it secure and never share it publicly.

**To generate a token:**
1. Go to **My Account > Settings > API**
2. Click **Generate New API Token**
3. Copy your token and store it securely

---

## Step 3: Choose Your Environment

OS Hub provides two environments for different use cases:

| Environment | Base URL | Purpose |
|------------|----------|---------|
| **Staging** | `https://staging.opensupplyhub.org/api/` | Testing and development. Data may be removed during regular cleanup. |
| **Production** | `https://opensupplyhub.org/api/` | Live data with regular moderation. Use for production applications. |

> **⚠️ Important:** Always test in the staging environment first, especially if you want to test posting data to OS Hub. Data moderation is regularly performed on production, and in the event that you send test traffic to the production environment, it may be removed.

---

## Step 4: Make Your First Request

Let's make a simple API request to search for a facility by OS ID.

GET /api/v1/production-locations/?os_id=IN2021079TDH72D

### Sample Response

```json
{
    "count": 1,
    "data": [
        {
            "country": {
                "alpha_3": "IND",
                "alpha_2": "IN",
                "name": "India",
                "numeric": "356"
            },
            "address": "No. 13, SM Road, SM Road, Near Ayyappa Temple, Jalahalli West, Bangalore - 560057, Karnataka, India.",
            "parent_company": "Not Applicable",
            "claim_status": "claimed",
            "os_id": "IN2021079TDH72D",
            "geocoded_location_type": "GEOMETRIC_CENTER",
            "minimum_order_quantity": "2000",
            "coordinates": {
                "lat": 13.0454318,
                "lng": 77.5218658
            },
            "description": "Our root in the textile industry started almost a decade ago with its first generation of experts who has helped us create YK Creation as it stands today. Our Journey which began as a small-scale industry with 70 machines and production capacity of 80,000 units per annum has expanded to a medium scale industry consisting of 200 machines with the production capacity of 550,000 units per annum. Our specialty lies in making the best garment in the industry especially casual trouser category. Our company motto is “We Strive, We Trust, We Aspire”. We “strive” for Quality products to sustain “trust” in our loyal customers and we “aspire” to improve continuously by commitment and dedication within our workforce. Quality is the real strength of the company, on which the foundation is built upon.",
            "affiliations": [
                "SEDEX"
            ],
            "local_name": "ವೈ.ಕೆ. ಕ್ರಿಯೇಷನ್",
            "percent_female_workers": 90,
            "claimed_at": "2024-06-15T08:32:29.014847Z",
            "product_type": [
                "Bottoms"
            ],
            "geocoded_address": "SM Rd, Ayyappa Nagar, Jalahalli West, Bengaluru, Karnataka 560015, India",
            "name": "YK Creation",
            "number_of_workers": {
                "min": 225,
                "max": 225
            },
            "sector": [
                "Apparel"
            ],
            "processing_type": [
                "Boarding"
            ],
            "average_lead_time": "45-60 days"
        }
    ]
}
```
---

## Next Steps

Now that you've made your first request, explore more capabilities:

### 📚 Learn More
- [API Reference](./API_REFERENCE.md) - Complete endpoint documentation
- [Authentication Guide](./AUTHENTICATION.md) - Security best practices
- [Rate Limits](./RATE_LIMITS.md) - Understand request limits
- [Error Handling](./ERROR_HANDLING.md) - Handle common errors

### 🎯 Common Use Cases
- [Searching Facilities](./guides/SEARCHING_FACILITIES.md)
- [Facility Matching](./guides/FACILITY_MATCHING.md)
- [Batch Processing](./guides/BATCH_PROCESSING.md)
- [Data Upload](./guides/DATA_UPLOAD.md)

### 🛠️ Tools & SDKs
- [Postman Collection](./tools/postman-collection.json)
- [Python SDK](./sdks/python/)
- [JavaScript SDK](./sdks/javascript/)

---

## Need Help?

**Resources:**
- **Documentation:** [Full API Documentation](./README.md)
- **Support:** [Contact OS Hub Support](https://opensupplyhub.org/support)
- **Community:** [OS Hub Developer Forum](https://forum.opensupplyhub.org)
- **Status:** [API Status Page](https://status.opensupplyhub.org)

**Common Issues:**
- [Troubleshooting Guide](./TROUBLESHOOTING.md)
- [FAQ](./FAQ.md)
