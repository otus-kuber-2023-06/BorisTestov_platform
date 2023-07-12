# Infrastructure Platform

Online Course by Otus @ June 2023

## Task 1

### Base

- Created and pulled a nginx-based Docker image:
    - The image serves port `8000`.
    - It has a specially tuned nginx configuration for this task.
    - The image name is `ormgair/nginx_exposed:0.1`.

- Created Pod web:
    - It is a Pod running a single main container based on the Docker image `ormgair/nginx_exposed:0.1` on port `8000`.
    - The default page is loaded through an `initContainer` using a script.
    - Both containers share a volume.

#### How to check

- Run `kubectl apply -f kubernetes-intro/web/web-pod.yaml`.
- Run `kubectl port-forward --address 0.0.0.0 pod/web 8000:8000`.
- Go to `localhost:8000`. You should see the default page content.

### Advanced

- Built and pulled the frontend image
  from [microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo).
- Created a yaml file to run a Pod from this image.
- Fixed runtime errors due to some uninitialized environment variables. The fixed manifest is saved to a separate file.

#### How to check

- Run `kubectl apply -f kubernetes-intro/frontend-pod-healthy.yaml`
- Run `kubectl get po frontend`
- You should see status `Running`

## Task 2

### Base

- Added `ReplicaSet` to `frontend` pod
- Created and pulled `paymentservice` image
- For `paymentservice`, added both `ReplicaSet` and `Deployment`
- Added `Probes` to `frontend-deployment`

### Advanced

- Created manifest for blue-green like scenario and reverse rolling update
- Created manifest for node-exporter

