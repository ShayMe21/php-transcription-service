# Audio Transcription Service (PHP Microservices with Laravel/Lumen)

### Prerequisites:
* PHP 7.1 or later
* Composer
* [Laravel/Lumen](https://lumen.laravel.com)
* [AWS Account](https://aws.amazon.com/) 
* [Auth0 Account](https://auth0.com/) 
* SMTP Email Provider (You can use Gmail's free [SMTP service](https://support.google.com/a/answer/176600?hl=en))

This sample app is a simulation of an audio transcription service. It consists of the following microservices:

* Transcription API Gateway - a service that exposes an API `POST /transcription` which accept a request to transcribe an audio file. Each new request is put on a `transcription queue` using AWS SQS to be handled asynchronously in the backend. API Requests are authenticated using Authorization Bearer HTTP header and Auth0's Machine to Machine [API Authorization](https://auth0.com/docs/api-auth).
* Transcriber service - an auto-scaling service that uses AWS SQS and multiple workers. Each worker listens to the queue for transcription requests, and when there is a new request, the first available worker takes it off the queue, transcribes the audio and puts the result on the `notification` queue.
* Notifier service - listens to the `notification` queue and when a transcription has been processed, it notifies the end user of the result via an email (for now). This could also be a push notification service on a native/web app.

The transcription and notifier services are not available publicly, they sit behind the Transcription API Gateway and communicate with each other and the SQS queues.

See individual Readme files in each service folder on how to setup and run each service.


### Screenshots:
1. Send a POST request to Transcription API.
![Transcription API](https://i.imgur.com/GvKgGC4.png)

2. Request is validated and sent to SQS.
![SQS](https://i.imgur.com/Pl8hx1h.png)

3. After processing, notifier service read the request from notifier queue and sends an email notification.
![Email notification](https://i.imgur.com/yo1lrG2.png)
