# Docker Swarm Guide.

### Swarm init and join commands.

- ``` docker swarm init --advertise-addr ${manager1Ip}:2377 --listen-addr ${manager1Ip}:2377 ```
- ``` docker swarm join --token ${manager-token} ${manager1Ip}:2377 --advertise-addr ${manager2Ip}:2377 --listen-addr ${manager2Ip}:2377 ```
- ``` docker swarm join --token ${worker-token} ${manager1Ip}:2377 --advertise-addr ${worker1Ip}:2377 --listen-addr ${worker1Ip}:2377 ```
