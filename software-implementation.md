# Software Implementation

The system was implemented using Python (Django) for the back-end and React for the front-end. Below are the key functionalities outlined in pseudocode.

## Patient Registration
```python
function register_patient(name, dob, address, etc.):
    if not validate_name(name):
        return "Invalid name"
    if not validate_dob(dob):
        return "Invalid date of birth"
    patient = Patient(name, dob, address, etc.)
    if patient.save():
        return "Patient registered successfully with ID: " + patient.id
    else:
        return "Registration failed"
## Appointment scheduling
function book_appointment(patient_id, doctor_id, date, time):
    if not is_doctor_available(doctor_id, date, time):
        return "Doctor not available at that time"
    appointment = Appointment(patient_id, doctor_id, date, time)
    if appointment.save():
        return "Appointment booked successfully"
    else:
        return "Booking failed"
## Checking system
function check_in(patient_id_or_dob):
    patient = find_patient_by_id_or_dob(patient_id_or_dob)
    if patient and patient.has_appointment_today():
        mark_patient_as_checked_in(patient)
        return "Checked in successfully"
    else:
        return "Check-in failed: Invalid patient or no appointment"
## Emergency surgery scheduling
function schedule_emergency_surgery(patient_id, surgery_type):
    if not is_operating_room_available():
        add_to_priority_queue(patient_id, surgery_type)
        return "Added to priority queue"
    surgeon = find_available_surgeon()
    if surgeon:
        schedule_surgery(patient_id, surgeon, surgery_type)
        return "Surgery scheduled"
    else:
        return "No available surgeon"

---

### **Example: `software-test-plan.md`**
```markdown
# Software Test Plan

Testing was conducted at multiple levels to ensure the system's reliability and functionality.

## Testing Levels
1. **Unit Testing**:
   - Tested individual functions like input validation and database queries.
   - Tools: `unittest` (Python), `Jest` (React).

2. **Integration Testing**:
   - Ensured components like appointment booking and doctor schedules interacted correctly.
   - Tools: `pytest` (Python), `React Testing Library`.

3. **System Testing**:
   - Simulated end-to-end workflows, such as patient registration to check-in.
   - Tools: `Selenium` for automated browser testing.

4. **User Acceptance Testing (UAT)**:
   - Involved receptionists and doctors to validate usability and functionality.
   - Feedback was used to refine the UI and workflows.

## Test Cases
| Test Case ID | Description                          | Expected Result                  |
|--------------|--------------------------------------|----------------------------------|
| TC001        | Patient registration with valid data | Patient registered successfully  |
| TC002        | Patient registration with invalid DOB| Error message: "Invalid DOB"     |
| TC003        | Book appointment with available slot | Appointment booked successfully  |
| TC004        | Book appointment with no available slot | Error message: "No slots available" |
