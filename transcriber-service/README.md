# Transcription Transcription Service

This service will  listen for new jobs on the transcription queue in SQS. When it gets a new file, it waits for 2 seconds (to simulate audio processing), and sends a new job on the notification queue.


### Setup
1. Make a copy of .env.example file: `cp .env.example .env` and fill in the details.
```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_QUEUE_URL_TRANSCRIBE=
AWS_QUEUE_URL_NOTIFY=
```
2. Run `composer install`
3. Then run `php worker.php`