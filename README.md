# AI-Adaptation-Framework
AI adaptation-to-target to deploy/operate AIs into special hardware, test and FPGA scenarios are available for demonstration

keyword: Flask-RESTX, RESTful API, Docker, Kubernetes, PostgreSQL HA Cluster (on K8s), Rabbitmq Cluster (on K8s), Celery

# Role
- client
- hardware provider
- AI Adaptation Service
- Delegate server (optional)

# usage
- hardware provider:
upload instruction, tools and data (with mannual page):
```
cd hw-provider
./upload -t <target_ID> -p <name_plan> -m <master_script_list> -s <sub_scripts_list>
```

- client:
List possible plan for target ID:
```
cd client
./list -t <target_ID>
```
Model adaptation-to-target(with mannual page):
```
cd client
./convert -t <target-ID> -p <name_plan> -d <preprossed_data_list> -m <original_model>
```

- conversion server
A docker container with tools integrate, using flask for receiving HTTP request.
Use convertor/rollout scripts to generate and deploy it on kubernetes!

```
cd convertor
./rollout <name_of_conversion_server> <version>
A local conversion server using flask is available for testing conversion and deployment features
```

- kubernetes
To deploy AI Adaptation service with its relevant components, use:
```
cd k8s
kubectl apply -f .
# after deployment ready
kubectl apply -f cluster
```
