#1 Start camunda docker
cd .\camunda-platform
docker-compose up

#2 Start rabbitmq docker
docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3.12-management

#3 Disable https in keycloak
#POSTGRES_DB: bitnami_keycloak
#POSTGRES_USER: bn_keycloak
#POSTGRES_PASSWORD: "#3]O?4RGj)DE7Z!9SA5"
update REALM set ssl_required = 'NONE' where id = 'master';

#4 Start the camunda process
#step-a
.\camunda-modeler/Camunda Modeler.exe
#step-b
Open .\Camunda\bpmn\order_fullfillment.bpmn in modeler
#step-c
deploy the bpmn diagram
#step-d
run the bpmn diagram

#5 Start Job Workers
cd .\app\microservice
dotnet run

#5 Start Integration Services
cd .\app\ProcessManager
dotnet run





