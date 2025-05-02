# Serverless for Email

## Overview

This module includes the `EmailHandler` class, an AWS Lambda function written in Java. It processes Amazon SNS (Simple Notification Service) events and sends email notifications using the **SendGrid API**. The function retrieves necessary configurations, such as the SendGrid domain and API key, from environment variables for secure and dynamic behavior.

## Functionality

The Lambda function performs the following tasks:

- Listens for incoming SNS events.
- Extracts and deserializes the message payload into an `EmailRequest` object.
- Sends an email using the SendGrid service via the `SendGridMessagesApi`.

## Key Components

### SendGridMessagesApi

An interface to interact with the SendGrid API for composing and sending emails.

### SNS Event Handling

Processes incoming records from SNS events and logs each message received.

### ObjectMapper

Used to convert the JSON-formatted SNS message into an `EmailRequest` object for internal use.
Once deployed, the Lambda function listens for incoming SNS events. Each event should contain a JSON payload structured as follows:

```json
{
  "recipient": "example@domain.com",
  "subject": "Your Subject Here",
  "message": "Your message body here"
}
```

### Environment Variables

These must be configured in the AWS Lambda environment:

- `SENDGRID_DOMAIN_NAME`: Your SendGrid-registered domain name.
- `SENDGRID_API_KEY`: API key used for authenticating with the SendGrid API.

## Build Instructions

To build the project and generate a JAR file for deployment:

```bash
mvn clean package

