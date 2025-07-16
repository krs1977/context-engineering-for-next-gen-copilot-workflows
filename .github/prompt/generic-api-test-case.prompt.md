# API Test Data Generation Prompt

Generate a comprehensive JSON array of test scenarios for data-driven API testing (e.g., Postman/Newman) for the following API module:

- **API Name**: [API_NAME] (e.g., "UserRoleManagement", "FileManagement", "Scheduler")
- **API Endpoints**: [LIST_OF_ENDPOINTS] (specify HTTP method and endpoint path)
- **API Description**: [API_DESCRIPTION] (brief overview)
- **Authentication Requirements**: [AUTH_TYPE] (e.g., Basic Auth, API keys, session tokens)
- **Required Parameters**: [PATH_PARAMS], [QUERY_PARAMS], [HEADERS], [REQUEST_BODY_SCHEMA]

**For each test scenario, include:**
- `TSName`: Descriptive scenario name
- `_comments`: Detailed purpose, expected behavior, validation points
- `_validation_type`: One of [RBAC +ve, RBAC -ve, Functional +ve, Functional -ve, Edge Case, Security]
- Required authentication fields (e.g., username, password, token)
- Endpoint-specific parameters as needed
- Response validation fields:
  - `responseCodeFor[EndpointName]`: HTTP status code
  - `responseTextFor[EndpointName]`: Expected response string or partial match

**Also include:**
- Edge cases (empty, null, invalid values)
- Security scenarios (invalid auth, injection attempts)
- Positive and negative tests for each endpoint
- Both valid and invalid users (e.g., admin, basic user, invalid user)

**Output must be:**
- Valid JSON array (Newman compatible)
- Each scenario fully self-contained and described

*Example format:*
```json
{
  "TSName": "Admin User Can Retrieve Roles",
  "_comments": "Test verifying admin can call GET /roles, expects HTTP 200 and valid roles list.",
  "_validation_type": "RBAC +ve",
  "username": "admin",
  "password": "password",
  "responseCodeForGetRoles": 200,
  "responseTextForGetRoles": "\"roles\":[{\"name\":\"Administrator\"}]"
}
