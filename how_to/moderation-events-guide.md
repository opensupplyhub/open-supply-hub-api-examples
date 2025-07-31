## Background

Open Supply Hub regularly performs **data moderation** to ensure the quality and accuracy of the data on the platform. As part of this process, when **duplicate facilities (OS IDs)** are identified, the OS Hub team **merges** them. After a merge, **only one OS ID remains active**, and the duplicate is deprecated.

## Why this is important for API users

If your system relies on OS IDs — especially for **collaboration with third-party organizations** — it's critical to keep your data **aligned with the most recent OS IDs**. Failing to do so may result in confusion or broken connections when an OS ID is merged.

## How to stay updated: Using the `/moderation-events/merge/` API endpoint

The `GET /moderation-events/merge/` endpoint allows you to retrieve a list of facilities that have been merged by the OS Hub Data Team.

Each record includes:
* `current_id`: the **active** OS ID that remains after the merge.
* `original_id`: the OS ID that was merged **into** the current_id (deprecated).
* `created_at`: the creation date of the original (now deprecated) OS ID.
* `merge_date`: the date when the merge took place.

**Sample response:**
```json
[
  {
    "current_id": "PL2023213ZGTRGT",
    "original_id": "PL2023214F95KZS",
    "created_at": "2023-08-02T08:55:10.046094Z",
    "merge_date": "2023-08-02T09:10:00.340169Z"
  },
  {
    "current_id": "PL2023213ZGTRGT",
    "original_id": "PL2023213T2T6FM",
    "created_at": "2023-08-01T11:35:31.595269Z",
    "merge_date": "2023-08-01T11:45:53.306978Z"
  }
]
````

## In practice:

* If you have the **original_id** in your system, you should **replace it with the current_id** to stay up to date.
* If you already have the **current_id** in your system, **no action is needed**.

## Recommended frequency for pulling updates:

Based on analysis of OS ID merges:
* **Daily or weekly calls** to `/moderation-events/merge/` are recommended to maintain updated OS IDs.
* You can use the `date_greater_than_or_equal` parameter to **limit results to recent merges**, optimizing performance.

## Note:

* If you are on a plan with a limited number of API calls, **this endpoint should not use up many of your allocated calls**. For example, **a single call** can retrieve **all moderation events from the past 1 to 3 weeks**, depending on the time frame you specify.
* **Daily queries** will not impact performance and ensure you have the most current data.
