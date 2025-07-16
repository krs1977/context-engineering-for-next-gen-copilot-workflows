
# Pentaho API Test Data Copilot Instructions

This repository uses a structured, prompt-driven approach to generate comprehensive test data for Pentaho API endpoints, ensuring full coverage and maintainability for Postman/Newman data-driven tests.

## How to Use

1. **Gather API Info**:  
   For each API module, collect:
   - API Name
   - Endpoints (method & path)
   - Description
   - Auth requirements
   - Required/requested parameters

2. **Generate Test Data**:  
   Use the prompt in [`.prompt.md`](./.prompt.md) with Copilot (or GPT-4) to auto-generate data arrays.

3. **Mandatory Fields** (for all scenarios):
   - `TSName`: Human-readable test scenario name
   - `_comments`: Scenario purpose, expected behavior, validation points
   - `_validation_type`: (e.g., RBAC +ve, Functional -ve, Security)
   - Authentication fields (`username`, `password`)
   - Endpoint-specific parameters as needed

4. **Validation Fields**:
   - `responseCodeFor[EndpointName]`
   - `responseTextFor[EndpointName]`
   - Naming: `[EndpointName]` is camelCase, e.g., `getUserRoles` → `responseCodeForGetUserRoles`

5. **Standard Test Users**:
   - `admin` / `password` (admin access)
   - `pat` / `password` (business analyst)
   - `bob` / `password` (power user)
   - `suzy` / `password` (end user)

   *Include invalid/special auth tests as described in this file.*

6. **Categories & Coverage**:
   - RBAC positive/negative, Functional positive/negative, Edge cases, Security (see details below)
   - Each endpoint and role must be covered with both success and failure tests

7. **Data Quality**:
   - Use realistic, valid Pentaho values
   - Follow naming conventions and JSON structure as in [`.prompt.md`](./.prompt.md)

8. **Quality Checklist**:
   - All fields present and formatted
   - Tests for all endpoints, users, and categories
   - Newman compatible output

## Categories & Examples

- **RBAC**: Test valid/invalid roles for each endpoint
- **Functional**: Test correct and incorrect input formats/types
- **Edge Cases**: Test null, empty, oversized, or special-character values
- **Security**: Test invalid auth, SQLi, XSS, path traversal

## Comments & Naming

- `_comments`:  
  `"Iteration-1 - Purpose - Expected Behavior - Validation Points"`
- `TSName`:  
  `"the Admin User Is Authorized"`, `"SQL Injection Prevention Test"`, etc.

## Output Example

See [`.prompt.md`](./.prompt.md) for the required data structure and example.

## References

- [Pentaho Documentation](https://help.hitachivantara.com/Documentation/Pentaho)
- [Postman/Newman Docs](https://www.postman.com/)
- [OpenAPI Spec](https://swagger.io/specification/)

