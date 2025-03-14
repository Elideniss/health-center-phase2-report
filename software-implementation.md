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

