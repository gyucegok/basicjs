# Basic NodeJS app

This is a Basic NodeJS app , ready for Google Cloud Funtions & Cloud Run & GKE

For a full demo, check;
https://codelabs.developers.google.com/codelabs/cloud-starting-cloudfunctions-v2

0-) Local run
npm i
npm run start

1-) Deploy Cloud Functions

gcloud beta functions deploy nodejs-http-func1 --gen2 --runtime nodejs16 --entry-point helloWorld --source . --region europe-west1 --trigger-http --timeout 600s

2-) build & push image
export IMAGE=europe-west1-docker.pkg.dev/gyucegok-alto/dock/basicjs
docker build ./src/ -t $IMAGE
docker push $IMAGE

3-) Deploy to Cloud runtime
gcloud config set run/region europe-west1
gcloud run deploy --image=$IMAGE

