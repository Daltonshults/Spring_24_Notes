<h1 align='center'>Endpoints</h1>
### POST `/active_workout/`
**Description**: Generates a workout for the user, and serves the data to the user.
Data: A list of song ids
```json
{ "songs": [ 1, 2, 3 ]
```
**Responses**: 
200:
```json
{
  "workout_set_songs": [
    {
      "artist": "string",
      "global_bpm": 120,
      "name": "string",
      "song_id": 1,
      "pixabayid": "string",
      "duration": 180,
      "segments": [
        {
          "start": 0,
          "stop": 30,
          "workout": "string",
          "is_static": true,
          "file_path": "string",
          "rep_locations": [10, 20, 30],
          "isRest": false
        }
      ]
    }
  ],
  "id": 1
}
```

500:
```json
{
  "error": "Internal server error"
}

```
### POST `/api/token/`
**Description:** Takes a set of user credentials and returns an access and refresh JSON web token pair to prove the authentication of those credentials.
**Data:**
```json
{ "username":
		{ "type": "string",
		"title": "string",
		"minLength": int },
		
	"password": { "type": "string",
		"title": "string",
		"minLength": int } 
}
```
**Response:**
201
```json
{
  "username": "string",
  "title": "string",
  "minLength": int,
  "password": "string",
  "title": "string",
  "minLength": int
}
```

### POST `api/token/refresh`
**Description:** Takes a refresh type JSON web token and returns an access type JSON web token if the refresh token is valid.
**Data:**
```json
{
  "refresh": "string"
}

```
**Responses:**
* 200
```json
{
  "refresh": "string",
  "access": "string"
}

```

### GET `/difficulty_bodysplit/`
**Description:** This endpoint is used to get the difficulty and body split for the client.
**Responses:**
* 200 
```json
{
  "songs": [
    [int]
  ],
  "difficulty": [int],
  "body_split": [int]
}
```
* 400
```json
{
	"error": "Bad request"
}
```
* 500
```json
{
	"error": "No difficulty or body split found"
}
```

### POST `/favorite_workout/`
**Description:** This endpoint allows a user to favorite a workout.
**Data**: 
```json
{
  "workout_id": int
}
```
**Responses:**
* 201
```json
{
  "status": "string"
}
```

* 500
```json
{
	"error": "Workout not found"
}
```

### GET `/get_audio/{song_id}`
**Description:** Serves an audio file.
**Parameters**: 
* song_id: used to retrieve the correct song
**Responses:**
* 200
```json
{
  "Content-Disposition": "string",
  "Content-Length": int
}
```

* 404
```json
{
	"error": "Error message"
}
```
* 500
```json
{
	"error": "Error message"
}
```

### GET `/home/`
**Description:** 
**Responses:**
* 200
```json
{
  "access_token": "string",
  "user_info": {
    "description": "User information",
    "first_name": "string",
    "last_name": "string",
    "name": "string",
    "email": "string",
    "new_user": "boolean"
  }
}
```


### GET `/logged_out`
**Description:** Logs out a user and returns their authentication status.
**Responses:** 
```json
{
  "message": "string",
  "status": "string"
}
```

### GET `/logout/`
**Description:** Logs out a user.
**Responses:** 301- Redirects user to `logged_out/`

### GET `saved_workouts/` 
**Description:** Get saved workouts for the current user.
**Responses:**
* 200
```json
{
  "total_duration": int,
  "workout_name": "string",
  "difficulty": "string",
  "created_by": "string",
  "body_split": "string",
  "songs_and_exercises": {
    "description": "string",
    "songs": [
      {
        "name": "string",
        "artist": "string",
        "duration": int,
        "song_id": int,
        "segments": {
          "description": "string",
          "stop": int,
          "start": int,
          "isRest": "boolean",
          "workout": "string",
          "file_path": int,
          "is_static": int,
          "rep_locations": [
            "string"
          ],
          "exercise_description": [
            "string"
          ]
        },
        "global_bpm": int
      }
    ]
  }
}
```
* 400
```json
{
	"error": "Bad request"
}
```
* 404
```json
{
	"error": "Workout not found"
}
```

### POST `/select_music/`
**Description:** This endpoint returns a list of songs that match the search query. The search search_type allows you to select which feature you want to search by. The query is the search term you want to use to search for songs.
**Data**: 
```json
{
  "search_type": "string",
  "query": "string"
}
```
**Responses:**
* 200
```json
{
  "songs": [
    {
      "description": "string",
      "name": "string",
      "artist": "string",
      "id": int,
      "pixabayid": int,
      "length": int,
      "uri": "string"
    }
  ]
}

```
* 500
```json
{
  "error": "string"
}
```

### GET `/share_workout/{workout_id}/`
**Description:** This endpoint allows a user to share a workout.
**Paramaters**: 
* `workout_id`: an integer used to recover the workout from the id
**Responses:**
* 200
```json
{
  "workout_name": "string",
  "workout_id": int,
  "difficulty": int,
  "body_split": int,
  "duration": int,
  "segments_and_exercises": {
    "description": "string",
    "start": int,
    "stop": int,
    "isRest": "boolean",
    "workout": "string",
    "file_path": "string",
    "is_static": "boolean",
    "rep_locations": [
      int
    ]
  }
}
```
* 404
```json
{
	"error": "Workout not found"
}
```

### GET `/token/`
**Description:** Redirects to the the application from Oauth2 login page.
**Responses:** 
* 200
```json
{
  "url_scheme": "string",
  "user_id": int,
  "user": "string",
  "name": "string",
  "access": "string",
  "nonce": "string",
  "refresh": "string"
}
```

### GET `/video/{video_name}`
**Description:**  Serves a video file.
**Paramaters**:
* `video_name`: a string representation of the file name
**Responses**: 
* 200
```json
{
  "Content-Disposition": "string",
  "Content-Length": int
}
```
* 404
```json
{
	"message": "Cannot be found"
}
```
* 500
```json
{
	"error": "Internal server error."
}
```


### GET `/workout_description/{workout_id}`
**Description:** Get the description of a workout by its ID.
**Paramaters:**
* `workout_id`: A integer that represents the id of the workout to get the description
**Responses:**
* 200
```json
{
  "total_duration": float,
  "workout_name": "string",
  "difficulty": "string",
  "created_by": "string",
  "body_split": "string",
  "songs_and_exercises": {
    "description": "string",
    "songs": [
      {
        "name": "string",
        "artist": "string",
        "duration": int,
        "song_id": int,
        "segments": {
          "description": "string",
          "stop": int,
          "start": int,
          "isRest": boolean,
          "workout": "string",
          "file_path": int,
          "is_static": boolean,
          "rep_locations": [
            "string"
          ],
          "exercise_description": [
            "string"
          ]
        },
        "global_bpm": int
      }
    ]
  }
}

```
* 500
```json
{
	"error": "Workout not found"
}
```