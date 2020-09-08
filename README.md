### start rabbitmq cluster
$ docker-compose -f docker-compose-cluster.yml



### check cluster status
$ docker exec -ti rabbitmq-node-1 bash -c "rabbitmqctl cluster_status"

### stopping the app for rabbit@rabbitmq-node-2:
$ docker exec -ti rabbitmq-node-2 bash -c "rabbitmqctl stop_app"

### join the cluster rabbit@rabbitmq-node-1:
$ docker exec -ti rabbitmq-node-2 bash -c "rabbitmqctl join_cluster rabbit@rabbitmq-node-1"

### start the app for rabbit@rabbitmq-node-2:
$ docker exec -ti rabbitmq-node-2 bash -c "rabbitmqctl start_app"

### check the cluster status again and verify that the node rabbitmq-node-2 successfully joined the cluster:
$ docker exec -ti rabbitmq-node-1 bash -c "rabbitmqctl cluster_status"

### the same steps for node rabbitmq-node-3:
$ docker exec -ti rabbitmq-node-3 bash -c "rabbitmqctl stop_app"
$ docker exec -ti rabbitmq-node-3 bash -c "rabbitmqctl join_cluster rabbit@rabbitmq-node-1"
$ docker exec -ti rabbitmq-node-3 bash -c "rabbitmqctl start_app"


### check cluster status 
$ docker exec -ti rabbitmq-node-1 bash -c "rabbitmqctl cluster_status"


### Connect to HA Proxy
http://localhost:1936/haproxy?stats
haproxy:haproxy

### Connect to RabbitMQ web ui
http://localhost:15672/

### RabbitMQ tutorials
https://www.rabbitmq.com/getstarted.html
