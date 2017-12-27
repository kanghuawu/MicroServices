# Google Cloud

## PubSub

### Resources

* [Google Cloud Pub/Sub Emulator](https://cloud.google.com/pubsub/docs/emulator)

* [Cloud Pub/Sub Client Libraries](https://cloud.google.com/pubsub/docs/reference/libraries#client-libraries-resources-go)

* [go client doc](https://godoc.org/golang.org/x/net/context)

* [pubsub tutorial](https://cloud.google.com/appengine/docs/flexible/python/writing-and-responding-to-pub-sub-messages#create_a_topic_and_subscription)

* [setup local emulator for testing](https://groups.google.com/forum/#!topic/cloud-pubsub-discuss/Kor-PHB1AcU)

* [pulling msgs](https://stackoverflow.com/questions/36552727/using-google-pubsub-with-golang-the-most-efficient-cost-way-to-poll-the-servi)

### Command
```
gcloud beta emulators pubsub start

gcloud beta emulators pubsub start --project=animated-axe-183700 --host-port=localhost:8050

gcloud beta emulators pubsub env-init

export PUBSUB_EMULATOR_HOST=localhost:8050
export GOOGLE_CLOUD_PROJECT=animated-axe-183700
export GOOGLE_CLOUD_PROJECT=bike-rental-system

gcloud beta pubsub topics create YOUR_TOPIC_NAME

gcloud beta pubsub topics create my-topic

gcloud beta pubsub subscriptions create YOUR_SUBSCRIPTION_NAME \
    --topic YOUR_TOPIC_NAME \
    --push-endpoint \
    https://YOUR_APP_ID.appspot.com/pubsub/push?token=YOUR_TOKEN \
    --ack-deadline 10

gcloud beta pubsub subscriptions create my-sub \
    --topic my-topic \
    --push-endpoint \
    http://localhost:3000/pubsub/push \
    --ack-deadline 30
```

### Rest
```
https://cloud.google.com/pubsub/docs/reference/rest/

// list all topics
GET localhost:8050/v1/projects/animated-axe-183700/topics

// list all subscriptions
GET /v1/{topic}/subscriptions

```

