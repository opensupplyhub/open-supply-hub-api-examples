# Building facility onboarding workfow - OS ID retrieval

## Use Case: 3rd party platforms Like amfori & ZDHC

A common use case for retrieving OS IDs involves platforms that use OS IDs as unique identifiers to facilitate data exchange and collaboration with third parties.

This is particularly relevant for large data holders with frequently changing databases, such as Multi-Stakeholder Initiatives (MSIs), Civil Society Organizations (CSOs), and major brands/retailers. These organizations onboard new facilities regularly and require a standardized, reliable way to track and match facility data.

- **Example amfori use case diagram:** [amfory sustainability platform](https://www.amfori.org/uploads/2025/06/Open-Supply-Hub-on-amfori-Sustainability-Platform-Guidance-for-Business-Partners.pdf)
- **Example Worldly/Higg platform:** [Account Registration](https://support.worldly.io/hc/en-us/articles/19418657651611-Account-Registration#h_01JMGGSADC12JWGH86YCJPJ40Q)

## How OS IDs Are Used

When onboarding a new supplier or facility, they are required to provide an OS ID to ensure accurate identification and data consistency across platforms.

### Finding an Existing OS ID

The supplier can search for their OS ID directly on OS Hub or through an API integration with the platform they are using.

### Creating a New OS ID (If No Match Exists)

If the facility is not yet listed in OS Hub, the supplier can generate a new OS ID either:

- Via the SLC form on the OS Hub website
- Via API integration with the third-party party platform

### Using OS IDs for Data Exchange

Many third-party platforms require suppliers to provide their OS ID to retrieve relevant facility data.

For example, amfori uses OS IDs to retrieve high-level aggregated results from the ZDHC Gateway within the amfori Sustainability Platform (see [case study](https://info.opensupplyhub.org/resources/amfori-case-study)).

## Recommended Workflow for Retrieving OS IDs (New API)

### Background on Single Location Contribution (SLC)

In Q1 2025, OS Hub introduced a new Single Location Contribution (SLC) workflow, allowing contributors with a small number of production locations to submit them directly via a web form. Unlike the traditional list upload method, this form accepts one location per submission, but users can submit multiple locations by filling out the form multiple times.

New API endpoints have been developed to support the SLC workflow and once they are released for external use, users will be able to build workflows using the new endpoints as well.

> **Important:** The old API will remain active, ensuring that any existing integrations will continue functioning.

### API Workflow Steps

The following steps outline the recommended API workflow for retrieving an OS ID. This process follows the Single Location Contribution (SLC) workflow used on the OS Hub website.

#### Step 1: Collect Facility Details

The user (new supplier/facility) provides key facility details: **name**, **address**, and **country**. This information can be collected via a form on the third-party platform.

#### Step 2: Search for an Existing OS ID

Make a `GET api/v1/production-locations/` request using the facility details provided to search the OS Hub database.

The API will return a list of potential matches based on the search criteria.

#### Step 3: Confirm an Existing Match or Create a New Location

The user can either confirm a match with an existing facility or create a new location in OS Hub.

##### Confirm a Match

- Use `PATCH api/v1/production-locations/` to confirm the match and update the facility details
- This API request also notifies OS Hub that the third-party platform is linked to the facility (i.e. is a data contributor)
- The response will contain the OS ID, which can be saved and displayed on the third-party platform

##### Create a New Location

- If no match is found, use `POST api/v1/production-locations/` to submit a new facility to OS Hub
- The response will include a **moderation ID** and **moderation status**, indicating that the request is pending review by the OS Hub Data Team
- The response will **not contain an OS ID** at this stage

#### Step 4: Check the Moderation Status for New Locations

If a new location was created, use `GET api/moderation-events/{moderation-id}/` to check the moderation status. Possible responses include:

- **PENDING** – The request is under review. Check the status again later
- **CREATED** – The OS ID has been successfully generated and is included in the response. Save it and display it on the third-party platform
- **REJECTED** – The submission was denied. The user should review the facility details and restart the process

## Workflow Diagram

![Retrieving OS IDs Workflow](Retrieving%20OS%20IDs.png)

---

## API Endpoints Summary

| Method | Endpoint | Purpose |
|--------|----------|---------|
| `GET` | `api/v1/production-locations/` | Search for existing facilities |
| `PATCH` | `api/v1/production-locations/` | Confirm match and update facility |
| `POST` | `api/v1/production-locations/` | Create new facility |
| `GET` | `api/moderation-events/{moderation-id}/` | Check moderation status |

## Status Codes

| Status | Description |
|--------|-------------|
| `PENDING` | Request under review |
| `CREATED` | OS ID successfully generated |
| `REJECTED` | Submission denied, review details |
