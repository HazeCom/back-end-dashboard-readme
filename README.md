## The user management module exposes the following endpoints:

* `POST /users/register`: Creates a new user.
``` json
{
  "userName": "John Doe",
  "email": "john.doe@example.com",
  "phone": "+15555555555"
}
```
* `POST /users/log-in`: Authenticates a user and sends an OTP.
```json
{
  "value":"provide valid email or phone",
}
```
* `POST /users/log-in?otp={otp}`: Pass the OTP as a request parem and returns the Authentication token.
* `GET /users/log-out`: Logs out the current user.
* `PATCH /users/update-profile`: Updates the current user's profile information.
```json
{
  "phone": "+15555555555",
  "ReferralCode": "TEST_CODE",
  "profileImage": "https://example.com/test.jpg",
  "dob": "1990-01-01",
  "graduation": "2010-01-01",
  "adharCard": false
}
```
* `GET /users/user-details`: Gets the details of the current user pass the authetication token.


## The course management module exposes the following endpoints:

- `POST /courses`: Creates a new course.
```json
{
  "title": "Software Engineering",
  "duration": "6 months",
  "imageUrl": "https://example.com/course-image.png",
  "courseTypes": "DA",
  "description": "This course will teach you the fundamentals of software engineering.",
  "batch": true,
}
```
- `GET /courses`: Gets all courses.
- `GET /user-course`: Gets all courses for the current user.
- `GET /user-course?courseId={courseId}`: Assign course to user by giving courseId.


## The Msat management module exposes the following routes;

- `POST /msat`: Create a new model.
``` json
[
  {
    "attempt": 1,
    "sub_section": {
      "sub_section_name": "Logical Thinking",
      "questions": [
        {
          "question_text": "If all cats are mammals, and all mammals are animals, then all cats are animals.",
          "options": [
            {
              "option_text": "True",
              "is_correct": true
            }
          ]
        }
      ]
    }
  }
]

```
- `GET /msat`: Get all models.
- `PATCH /score`: Calculate the score, pass sub_sectionId and option_id to calcuate the score.
```json
{
  "sub_sectionId": "your_sub_section_id",
  "option_id": "your_option_id"
}

```
- `PATCH /register-msat/:msatId`: Register an msat pass the msatId in the url to regist the user with the msat.
- `GET /user-score`: Get the user score.


## The Activity management module exposes the following routes.

- **POST /activities**: Create a new activity.
```json
{
  "title": "Your activity title",
  "aboutEvent": "Description of the event",
  "aboutSpeaker": "Description of the speaker",
  "type": true,
  "instructor_name": "Name of the instructor",
  "photoUrl": "URL of the photo",
  "startDate": "Start date of the activity",
  "endDate": "End date of the activity",
  "register": false,
  "vedioUrl": "URL of the video",
  "zoomlink": "Zoom link for the activity",
  "peopleRegistered": 0,
}

```
- `GET /activities`: Get all activities.
- `GET /activities/:activityId`: Get an activity by ID.
- `DELETE /activities/:activityId`: Delete an activity.
- `PATCH /register-activity?activityId={activityId}`: Register an activity (requires authentication).
