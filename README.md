# Basic NodeJS app

This is a Basic NodeJS app , ready for Google Cloud Funtions & Cloud Run & GKE


Local run

```
npm i
npm run start
```

Deploy Cloud Functions

```
gcloud beta functions deploy nodejs-http-func1 --gen2 --runtime nodejs16 \
--entry-point helloWorld --source . --region europe-west1 --trigger-http --timeout 600s
```

Build & push image

```
export IMAGE=europe-west1-docker.pkg.dev/gyucegok-alto/dock/basicjs
docker build ./src/ -t $IMAGE
docker push $IMAGE
```

Deploy to Cloud runtime

```
gcloud config set run/region europe-west1
gcloud run deploy --image=$IMAGE
```

GKE Autopilot

```
kubectx
kubectl apply -f ./kubernetes-manifests/basicjsdeploy.yaml
kubectl apply -f ./kubernetes-manifests/basicjssvc.yaml
```
