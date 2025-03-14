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
