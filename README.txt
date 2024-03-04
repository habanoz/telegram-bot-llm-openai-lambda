
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

### Deployment

Deploy with following command.

```bash
chalice deploy
```