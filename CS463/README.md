# algorhythms

## Future Work

### Algorithm
- Simplify the audio feature extraction process since it bottlenecks the algorithm
    - Custom built feature extraction functions with NumPy should be faster than librosa
    - Possibly refactor algorithm into C++ for parallel processing of features 
- Test the algorithm with different changes based on TODO's in the code

### Django

### Frontend Flutter Application
- Set up the Flutter app to work on iOS
    - Need to use MP3 instead of ogg
    - On first login, iOS prompts for Nginx username and password. The requirement should be removed from the server and a different method for securing communication between the API and the app (such as an API key)
- Make the app responsive (portrait, landscape, large monitors)
- Incorporate audio prompts so the user doesn’t have to look at their phone while working out
- Once a new SSL certificate is set up in the production environment, update the API manager class to use the new certificate
- Fix Known Bugs
    - Attempting to play ogg audio files when the app is running on iOS results in this error: `PlayerException ((-11828) Cannot Open)`
        - This is likely caused by trying to play ogg files instead of mp3 files. It would be worth trying to play an mp3 file downloaded from the AlgoRhythms server and see if the error goes away.
    - If you select music, and then search on the select music screen, the selected song is changed.
    - If the segment is a rest segment, the workout description page still shows a workout for it

### Production Environment
- Add non self signed SSL certificate using AWS Certificate Manager
- Overhaul production environment:
    - Possibly use AWS API Gateway, Lambdas, S3, and EC2 instances to improve scalability
        - The lambdas can start up and run an EC2 instance with the algorithm and then shut down the instance after the algorithm is done running
        - The database can be refactored into a NoSQL DynamoDB database w/ an S3 instance for audio and video files
- Add a CI/CD pipeline using AWS CodePipeline and CodeBuild, or simply a script that pulls the repository
    - The gunicorn server restarts automatically when changes are made to the Django app
- Improve the monitoring system (currently using builtin gunicorn/nginx logging)
    - Add alerts for disaster events
- Add some sort of load balancing before releasing the application
- Add a backup system for the database, or use a managed database service

## Documentation
- [Documentation](./documentation/)
- Documentation .html files should be viewed in a browser after pulling the repository
- `./generate_docs.sh` to generate documentation for algorithm files

## Song Segmenter Algorithm
### Description
This algorithm takes a song and splits it into segments of similar energy and approximately a given length. The outputs are the segments and their corresponding start and end times, with other metadata added for connection with the backend. The segments optimize both timbral similarity and length, attempting to find segments of 2:1 length ratio with similar timbral features.
### Usage
- `python pipeline_automated.py </path/songid.ogg>`
### Documentation
- [Audio Analyzer](./documentation/python/audio_analyzer.html)
- [Song Segmenter](./documentation/python/song_segmenter.html)
- [Beat Boundaries](./documentation/python/beat_boundaries.html)
- [Cluster Output](./documentation/python/cluster_output.html)
- [Metrics](./documentation/python/metrics.html)

## Production Scripts
- [Output Adder](./documentation/python/production_files/output_adder.html)
- [Metadata Adder](./documentation/python/production_files/metadata_adder.html)
- [Listener](./documentation/python/production_files/listener.html)

## Scraping Scripts
- [PixaBay Scraper](./documentation/python/scraping/pixabay_scraper.html)
- [Genre Artist Scraper](./documentation/python/scraping/genre_artist_scraper.html)
- [File Transfer](./documentation/python/scraping/file_transfer.html)
- [Audio File Converter](./documentation/python/scraping/audio_file_converter.html)

## Flutter Application
### Description
The Flutter application is a mobile app that allows users to generate interactive workouts to music. It connects to the backend to retrieve workout data, and then displays it in the application.
- [Application API](./documentation/flutter_app/index.html)
- [Flutter README](./flutter/algorhythms/README.md)
- [User Instructions](./flutter/algorhythms/user_instructions.md)

## Production Environment
- [Documentation README](./documentation/README.md)

## Django API
### Description
The worst api anyone has ever built
- [API Documentation](./documentation/django/Endpoints.md)
- [API Environment](./documentation/django/Setting Up Django Dev Environment.md)
- [Swagger](./documentation/django/Getting The Swagger Documentation.md)
- [Database](./documentation/django/Database Documentation.md)
