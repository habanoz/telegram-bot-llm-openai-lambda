# Telegram Bot

This is a Telegram Chat Bot that is designed to work on AWS Lambda. OpenAI models are used to generate responses. This is not a real chatbot because chat history is not provided to the chat model. 

Chalice framework is used to deploy the application to AWS Lambda.

Check out my [blog post](https://habanoz.github.io/tech-feed/analysis/aws-lambda-llm-telegram-bot/) about this work.

## AWS CLI

Here are resources to prepare the AWS environment.

[Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

[Configure AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-quickstart.html)

Also ensure that required permissions are provided. 

### Local Testing

Start local chalice server.

```bash
export TELEGRAM_TOKEN=<YOUR_TELEGRAM_TOKEN>
export OPENAI_API_KEY=<YOUR_OPENAI_API_KEY>
chalice local
```

Send your request. 

```bash
curl -H "Content-Type: application/json" "http://localhost:8000/" -d  @test/sample_events/message_event.json
```
For a chat definition, you may send a message to the bot and check AWS lambda logs for the event definitions. It is best if you replace file content with the event definition from the logs. You may need to modify the formatting of the event definition to have a valid JSON document.

### Deployment

Deploy with the following command.

```bash
chalice deploy
```

Please note that you will need to create and set environment variables in the AWS lambda console.

## Telegram Configuration

Use the renowned BotFather to obtain a telegram token. 

Update telegram webhook (After obtaining a lambda function URL):
```bash
curl https://api.telegram.org/bot<TELEGRAM_TOKEN>/setWebHook?url=<LAMBDA_FUNCTION_URL>
```

Get web hook processing info e.g. last errors.
```bash
curl https://api.telegram.org/bot<TELEGRAM_TOKEN>/getWebHookInfo
```
