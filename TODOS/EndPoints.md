### With Token Auth
* `home/`
* `difficulty_bodysplit/`
* `workout_description/<intLworkout_id>/`
* `saved_workouts/`
* `share_workout/<intLworkout_id>/`
* `favorite_workout/`
* `api/token/` 
	* Requires refresh
* `api/token/refresh/`
	* Need to be able to send tokens to this endpoint, but might want it to be protected
* `select_music/`

### Without Token Auth
* `token/`
* `loggout/`
* `logged_out/`
* `favicon.ico`
* `error/`
* `auth/login/<oauth2 provider>`

### Swagger:
* These should not be available within the production environment, and we can turn them off by commenting them out, or removing them.
* Unless you can think of a reason that we need this in production?