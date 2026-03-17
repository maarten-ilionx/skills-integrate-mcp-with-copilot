# Mergington High School Activities API

A super simple FastAPI application that allows students to view and sign up for extracurricular activities.

## Features

- View all available extracurricular activities
- Sign up for activities (teacher login required)
- Unregister students from activities (teacher login required)
- Session-based teacher authentication stored in `teachers.json`

## Getting Started

1. Install the dependencies:

   ```
   pip install -r ../requirements.txt
   ```

2. Run the application:

   ```
   python app.py
   ```

3. Open your browser and go to:
   - API documentation: http://localhost:8000/docs
   - Alternative documentation: http://localhost:8000/redoc

## API Endpoints

| Method | Endpoint                                                          | Description                                                         |
| ------ | ----------------------------------------------------------------- | ------------------------------------------------------------------- |
| GET    | `/activities`                                                     | Get all activities with their details and current participant count |
| POST   | `/activities/{activity_name}/signup?email=student@mergington.edu` | Register a student (teacher only)                                   |
| DELETE | `/activities/{activity_name}/unregister?email=student@mergington.edu` | Unregister a student (teacher only)                             |
| POST   | `/auth/login`                                                     | Teacher login (JSON body with username and password)                |
| POST   | `/auth/logout`                                                    | Teacher logout                                                      |
| GET    | `/auth/status`                                                    | Get current teacher login status                                    |

## Teacher credentials

Teacher usernames and passwords are stored in:

`teachers.json`

Demo accounts:

- `ms.johnson` / `Teach3rPass!`
- `mr.lee` / `CoachPass123`

## Data Model

The application uses a simple data model with meaningful identifiers:

1. **Activities** - Uses activity name as identifier:

   - Description
   - Schedule
   - Maximum number of participants allowed
   - List of student emails who are signed up

2. **Students** - Uses email as identifier:
   - Name
   - Grade level

All data is stored in memory, which means data will be reset when the server restarts.
