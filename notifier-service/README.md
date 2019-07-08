# Transcription Notification Service

This service will endlessly listen for new jobs on the notification queue in SQS. When it receives a new job, it sends an email to the email address specified in the `user-email` field of the message.


### Setup
1. Make a copy of .env.example file: `cp .env.example .env` and fill in the details.
```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_QUEUE_URL_TRANSCRIBE=
AWS_QUEUE_URL_NOTIFY=

SMTP_HOST=
SMTP_USERNAME=
SMTP_PASSWORD=
```
2. Run `composer install`
3. Then run `php worker.php`