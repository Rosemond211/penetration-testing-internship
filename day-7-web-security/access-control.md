# Access Control / IDOR Lab

## Lab
User ID controlled by request parameter

## Normal Request
GET /my-account?id=wiener

## Test
The `id` parameter was changed from:

wiener

to:

carlos

## Result
The application returned Carlos's account instead of restricting access to the authenticated user. The lab was successfully solved by submitting the API key displayed in Carlos's account.

## Vulnerable Behavior
The application trusted the user-controlled `id` parameter when selecting an account and did not properly verify authorization.

## Impact
An attacker could access another user's account information by changing the identifier in the request.

## Prevention
The server should enforce authorization for every object requested. Do not rely on user-controlled identifiers alone. Verify that the authenticated user is authorized to access the requested account.

