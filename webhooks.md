# What Is a Webhook?

A webhook is like someone knocking on your door to deliver a message as soon as something happens.

Example:

Let’s say you have an app that integrates with Slack.

A user sends a message in a Slack channel.

Slack instantly calls your API (https://yourapp.com/webhook) with the message data.

That call is the webhook.


Key Points:

Webhooks are HTTP POST requests.

They are event-driven: only triggered when something happens.

Your system must have a public API endpoint to receive them.


Sample Payload (from Slack or Stripe):

{
  "event": "message.posted",
  "data": {
    "text": "Hello!",
    "user": "U123456"
  }
}

Simple Flask Receiver:

@app.route('/webhook', methods=['POST'])
def webhook():
    data = request.json
    print("Received:", data)
    return '', 200
