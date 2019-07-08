# Transcription Gateway API

This service exposes a single API endpoint `POST /transcription` and receives job requests to process audio files. It validates requests and ensures Authorized API access by decoding/verifying the JWT Access Token in the Authorization Header. It finally puts a new job on the transcription queue for the Transcription service to read and process it. 


### Setup
1. Make a copy of .env.example file: `cp .env.example .env` and fill in the below details.
```
CLIENT_ID=
CLIENT_SECRET=
ISSUER=
AUDIENCE=
REDIRECT_URI=
SCOPE=

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_QUEUE_URL_TRANSCRIBE=
```
2. Install dependencies: `composer install`
3. Run the service: `php -S 127.0.0.1:8080 -t public`
