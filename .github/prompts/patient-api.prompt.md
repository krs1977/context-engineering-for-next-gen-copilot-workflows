## API Endpoint: Patient Creation (Frappe Healthcare)

Generate comprehensive JSON test scenarios for this API endpoint:

- **API Name:** Frappe Healthcare - Patient
- **Endpoint:** `POST /api/resource/Patient`
- **Description:** Create a new patient record in Frappe Healthcare.
- **Authentication:** Basic Auth (username/password)
- **Required Body Parameters:**
  - `patient_name` (string) — Full name of the patient
  - `gender` (string, enum: "Male", "Female", "Other")
  - `date_of_birth` (string, ISO date format)
  - `mobile` (string, optional)
  - `email` (string, optional)
  - `blood_group` (string, enum: "A+", "A-", "B+", "B-", "AB+", "AB-", "O+", "O-", optional)
  - (Other fields as per Frappe Healthcare Patient DocType)

- **Expected Responses:**
  - **201 Created:** Returns patient JSON on success
  - **400 Bad Request:** Missing/invalid required fields
  - **409 Conflict:** Patient with same identifier/email already exists

- **Validation fields (per scenario):**
  - `responseCodeForCreatePatient` (expected HTTP status)
  - `responseTextForCreatePatient` (key part of success or error message/JSON)

**Test Data Must Include:**
- Positive scenario: Valid patient creation
- Negative scenarios:
  - Missing required fields (`patient_name`, `gender`, `date_of_birth`)
  - Invalid `gender` value (not in enum)
  - Duplicate patient (reuse unique field, e.g., email)
  - Invalid email format
- Edge cases: Empty strings, special characters, max/min lengths
- Security: Injection attempts in `patient_name` or `email`

**Test user:**  
Use Frappe standard test user or admin credentials (`Administrator` / `admin`).

**Output format:**  
- JSON array, one object per test scenario, ready for Newman/Postman data-driven test
- Example fields:

```json
{
  "TSName": "Valid patient creation",
  "_comments": "Test successful creation of a patient with all valid fields.",
  "_validation_type": "Functional +ve",
  "username": "Administrator",
  "password": "admin",
  "body": {
    "patient_name": "John Doe",
    "gender": "Male",
    "date_of_birth": "1990-05-25",
    "mobile": "9876543210",
    "email": "john.doe@example.com",
    "blood_group": "A+"
  },
  "responseCodeForCreatePatient": 201,
  "responseTextForCreatePatient": "\"patient_name\":\"John Doe\""
}
