---

Bug: API requests occasionally return empty responses despite receiving HTTP 200.

RubberDuck: The request handler successfully sends the request and receives a successful HTTP status code. However, the response parser assumes that the response body always contains a populated "content" field.

The API can legitimately return an empty response, particularly when generation is interrupted, no output is produced, or the provider returns an unexpected response structure.

The parser currently accesses "response.content[0].text" without checking whether "content" exists, whether the array contains elements, or whether the first element contains text.

This means the HTTP request itself succeeds, but the application subsequently processes an invalid or empty response and returns an empty string to the caller.

The problem is therefore not necessarily in the network request. It is potentially in the response validation and extraction logic.

Review: The response parser needs validation before attempting to extract generated text.

Changes made:

- Added checks for missing or empty "content" arrays.
- Added validation for the first content element.
- Added handling for unexpected response structures.
- Added logging to distinguish successful empty responses from parsing failures.

The HTTP 200 status is no longer treated as sufficient evidence that usable generated text exists.

---

Bug: Repeated button clicks trigger multiple simultaneous database submissions.

RubberDuck: The submission button calls an asynchronous function that sends the current form data to the database.

However, the button remains enabled while the request is being processed. Because the operation is asynchronous, users can click the button multiple times before the first request finishes.

Each click starts another independent database operation. This can result in duplicate records being created, inconsistent application state, and unnecessary database traffic.

The underlying issue is that the application does not track whether a submission is already in progress.

Disabling the button visually is not sufficient unless the submission handler itself also prevents duplicate execution. Otherwise, multiple events could still reach the handler before the interface updates.

Review: Added an explicit submission state and an early-return guard inside the submission handler.

Changes made:

- Introduced an "isSubmitting" state.
- Prevented additional submissions while an existing request is processing.
- Disabled the submission button during processing.
- Restored the button state after the request completes, including when an error occurs.
- Added error handling so failed requests do not leave the interface permanently locked.

The submission handler now independently enforces the single-submission rule rather than relying exclusively on the button's visual state.

---