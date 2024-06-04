# Music Database Models Documentation

This documentation provides an overview of the models used in the music database. Each section explains the purpose of the model, its attributes, and other relevant details to help understand the structure and functionality of the database.

## Table of Contents

- [Genre](#genre)
- [Artist](#artist)
- [Album](#album)
- [BaseSong](#basesong)
- [Song](#song)
- [TestSong](#testsong)
- [User](#user)
- [BodySplit](#bodysplit)
- [Difficulty](#difficulty)
- [Impact](#impact)
- [Exercise](#exercise)
- [Workout](#workout)
- [WorkoutPlaylist](#workoutplaylist)

## Genre

### Purpose:
Categorizes music tracks or albums by their stylistic qualities.

### Attributes:
- **id:** Unique identifier for the genre.
- **name:** Name of the music genre (e.g., Rock, Jazz, Classical).

### Notes:
- Helps in organizing and discovering music based on listener preferences.

## Artist

### Purpose:
Represents a musical artist or band.

### Attributes:
- **id:** Unique identifier for the artist.
- **name:** Name of the artist or band.

### Notes:
- Useful for cataloging and searching music by artist.

## Album

### Purpose:
Represents music albums.

### Attributes:
- **id:** Unique identifier for the album.
- **title:** Title of the album.
- **artist:** Foreign key linking to the Artist model.

### Notes:
- Facilitates easy access and organization of albums.

## BaseSong

### Purpose:
Represents individual songs with detailed information.

### Attributes:
- **id:** Unique identifier for the song.
- **pixabayid:** ID for Pixabay reference.
- **name:** Name of the song.
- **artist:** Foreign key linking to the Artist model.
- **album:** Foreign key linking to the Album model (nullable).
- **duration:** Length of the song in seconds.
- **genre:** Many-to-many relationship with the Genre model.
- **file_path:** File path where the song is stored.
- **added_date:** Date and time when the song was added.

### Notes:
- Stores metadata, file paths, and other relevant data about each song.

## Song

### Purpose:
Extends the BaseSong model with additional attributes.

### Attributes:
- **global_bpm:** Global beats per minute of the song.
- **sample_rate:** Sample rate of the song (default 22050 Hz).
- **pure_segments:** JSON field storing algorithmically determined pure segments of the song.
- **clustered_segments:** JSON field storing algorithmically determined clustered segments of the song.

## TestSong

### Purpose:
Represents a simplified format of a song for testing purposes.

### Attributes:
- **name:** Name of the song.
- **artist:** Name of the artist or band.

### Notes:
- Used in testing environments or for simple applications.

## User

### Purpose:
Extends the default Django User model with additional fields.

### Attributes:
- **id:** Unique identifier for the user.
- **trainer:** Boolean indicating whether the user is a trainer (default False).
- **groups:** Many-to-many relationship with the Group model.
- **user_permissions:** Many-to-many relationship with the Permission model.

### Notes:
- Adds custom fields for distinguishing between regular users and trainers.
- Allows for more nuanced access control and group management.

## BodySplit

### Purpose:
Categorizes workouts based on the part of the body they target.

### Choices:
- **UPPER:** Upper body workouts.
- **LOWER:** Lower body workouts.
- **CORE:** Core muscle workouts.

### Notes:
- Used within models to define fields specifying targeted body parts.

## Difficulty

### Purpose:
Categorizes workouts based on their difficulty level.

### Choices:
- **BEGINNER:** Easy workouts.
- **INTERMEDIATE:** Medium-difficulty workouts.
- **ADVANCED:** Hard workouts.

### Notes:
- Helps users filter and select workouts based on their preferred challenge level.

## Impact

### Purpose:
Represents the impact level of a workout.

### Choices:
- **LOW:** Low impact.
- **MEDIUM:** Medium impact.
- **HIGH:** High impact.

## Exercise

### Purpose:
Represents an exercise with detailed information.

### Attributes:
- **id:** Unique identifier for the exercise.
- **exercise_name:** Name of the exercise.
- **difficulty:** Difficulty level of the exercise.
- **average_rep_time:** Average time per repetition.
- **bpm_timing:** Beats per minute timing.
- **description:** JSON field describing the exercise.
- **body_split:** Integer field representing the targeted body part.
- **double_sided:** Boolean indicating if the exercise targets both sides.
- **static:** Boolean indicating if the exercise is static.
- **side_switch:** Boolean indicating if side switching is required.
- **equipment:** Boolean indicating if equipment is needed.
- **impact:** Impact level of the exercise.
- **file_path:** File path where the exercise is stored.

### Notes:
- Categorizes and accesses exercises based on these attributes.

## Workout

### Purpose:
Represents a workout with detailed information.

### Attributes:
- **id:** Unique identifier for the workout.
- **duration:** Duration of the workout.
- **segments_and_exercises:** JSON field storing segments and exercises.
- **exercises:** Many-to-many relationship with the Exercise model.
- **song_id:** Foreign key linking to the Song model.

### Notes:
- Organizes and manages individual workouts.

## WorkoutPlaylist

### Purpose:
Stores a collection of workouts in a playlist format.

### Attributes:
- **id:** Unique identifier for the playlist.
- **name:** Name of the playlist (default "Workout Playlist").
- **duration:** Total duration of the playlist.
- **segments_and_exercises:** JSON field storing segments and exercises.
- **difficulty:** Aggregate difficulty level for the playlist.
- **body_split:** Integer field representing the primary body split focus.
- **creation_date:** Date and time when the playlist was created.
- **created_by:** Foreign key linking to the User model.
- **is_favorite:** Boolean indicating if the playlist is a favorite.
- **workouts:** Many-to-many relationship with the Workout model.
- **workout_ids_ordered:** Ordered list of workout IDs.

### Notes:
- Groups multiple workouts together, allowing for easy management and organization of workout playlists.