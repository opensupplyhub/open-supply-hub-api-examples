# Deactivate Facilities or Lists

Remove (anonymize) your contributor name from facilities you no longer source from, without uploading a replacement list or contacting the OS Hub team.

| I want to… | Endpoint | Scope |
|---|---|---|
| Deactivate **one facility** | `POST /api/facilities/{os_id}/dissociate/` | All of your contributions to that facility |
| Deactivate **all facilities in a list** | `POST /api/facility-lists/{list_id}/deactivate/` | Every facility in that list |

Note: Both endpoints are on the **legacy API**. They are not available on `/api/v1/production-locations/`.

> [!IMPORTANT]
> **This is not deletion.** Facilities and their data stay on OS Hub. Your contributor name is replaced with your contributor type (for example, `Brand A` becomes `One Brand/Retailer`). This is the same anonymization OS Hub applies when a contributor deactivate a facility or list via their OS Hub account or emailing the OS Hub Team.

## Before you start

- **API token** for a registered account with a confirmed email. Send it as `Authorization: Token <your_token>`.
- **Your own data only.** You can only dissociate or deactivate contributions made by your account.
- **No request body.** Both endpoints take an ID in the path and nothing else.

| Environment | Base URL |
|---|---|
| Production | `https://opensupplyhub.org` |
| Staging | `https://staging.opensupplyhub.org` |

Test on staging first. Neither action can be undone through the API.

---

## Deactivate a single facility

```
POST /api/facilities/{os_id}/dissociate/
```

Deactivates **all** of your matches to that facility, across every list or single-facility upload you have made. Your other facilities are unaffected.

### Request

```bash
curl -X POST "https://opensupplyhub.org/api/facilities/CN2019303BQ3FX0/dissociate/" \
  -H "Authorization: Token YOUR_API_TOKEN"
```

### Response — `200 OK`

Returns the updated facility record (same format as `GET /api/facilities/{os_id}/`). Check `properties.contributors` to confirm your name now appears as your contributor type.

```json
{
  "id": "CN2019303BQ3FX0",
  "type": "Feature",
  "properties": {
    "os_id": "CN2019303BQ3FX0",
    "name": "Example Garment Factory",
    "contributors": [
      { "id": 2, "name": "One Brand/Retailer", "is_verified": false },
      { "id": 3, "name": "An MSI", "is_verified": false }
    ]
  }
}
```

> [!NOTE]
> If you have no active contributions to the facility, the call still returns `200` with the facility unchanged. Compare `contributors` before and after if you need to confirm a change happened.

### The facility is displayed as "REMOVED" in the contributor's account:

<img width="1379" height="433" alt="Screenshot 2026-11-03 at 15 05 17" src="https://github.com/user-attachments/assets/55164467-2dd8-4ad2-a1f3-afd2f30baf24" />

<img width="1379" height="433" alt="Screenshot 2026-11-03 at 15 07 06" src="https://github.com/user-attachments/assets/6a5a395f-1123-442a-b418-07b1166fe5ae" />

---

## Deactivate a list

```
POST /api/facility-lists/{list_id}/deactivate/
```

Anonymizes your contribution on **every** facility in the list in one call. In the contributor account, the list status changes to `Feedback Phase` with the reason *"Deactivated by the contributor."*
<img width="1506" height="801" alt="Screenshot 2026-11-03 at 17 15 15" src="https://github.com/user-attachments/assets/bb2f4c62-6e3c-4730-beaa-dfc8cbdb9520" />


### Step 1 — Find the list ID

```
GET /api/contributor-lists-sorted/?contributors={contributor_id}
```

Returns your active, approved lists, newest first. Every list returned can be deactivated.

```bash
curl "https://opensupplyhub.org/api/contributor-lists-sorted/?contributors=1234" \
  -H "Authorization: Token YOUR_API_TOKEN"
```

```json
[
  { "id": 16, "name": "2026 Q1 Suppliers" },
  { "id": 15, "name": "2025 Q4 Suppliers" }
]
```

> [!NOTE]
> Don't know your contributor ID? Find your organization's name in `GET /api/contributors/`, which returns `[id, name]` pairs.
>
> Responses are cached for up to 10 minutes, so a list you've just deactivated may still appear here briefly.

### Step 2 — Deactivate it

```bash
curl -X POST "https://opensupplyhub.org/api/facility-lists/15/deactivate/" \
  -H "Authorization: Token YOUR_API_TOKEN"
```

### Response — `200 OK`

```json
{
  "list_id": 15,
  "deactivated": true
}
```

---

## Errors

Errors return a JSON body with a `detail` field. No changes are made when an error is returned.

| Status | Endpoint | Cause |
|---|---|---|
| `401` / `403` | Both | Missing or invalid token, or account email not confirmed |
| `404` | Dissociate | OS ID does not exist |
| `404` | Deactivate | `The list with the given id was not found.` — list doesn't exist **or belongs to another contributor** |
| `404` | Deactivate | `This list is already inactive.` |
| `400` | Deactivate | `Only an approved list can be deactivated.` — list is still pending or was rejected by moderation |

---

## FAQ

**Are the facilities deleted?**
No. Facilities, their OS IDs, and other contributors' data stay on the platform. Only the link to your name is hidden.

**What do other users see afterwards?**
Your contributor type instead of your name, for example `One Brand/Retailer`. This applies to the facility profile, API responses, and downloads.

**Can I undo a deactivation or dissociation?**
Not through the API. To reappear on a facility, upload it again (as a list or via `POST /api/facilities/`).

**I deactivated a list, but my name still shows on one of its facilities. Why?**
You also contributed that facility through another active list or upload. Use the dissociate endpoint to remove it everywhere.

**Should I dissociate facility by facility or deactivate the list?**
If a whole upload is out of date, deactivate the list: it's a single call. Use dissociate to remove individual suppliers while keeping the rest of the list active.

**Is this available on the v1 API?**
Not yet. Use the legacy endpoints above.
