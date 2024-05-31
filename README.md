# Docker Swarm practice for Fanap Campus

the setup is easy, actually.
we only need to have 2 linux machines with docker installed.

1. we execute this command on the first machine:

    ```txt
    docker swarm init 
    ```

    or if you have multiple interfaces with multiple ip's   you get error when you wanna init the cluster, you    should choose one interface/ip and init using that     address as --advertise-addr, like this:

    ```txt
    docker swarm init --advertise-addr masterip
    ```

    which outputs a join command for the worker node to join the swarm cluster:

    ```txt
    docker swarm join --token mytoken masterip:2377
    ```

2. check if the node(s) have successfully joined the cluster.

   ```txt
   docker node ls
   ```

3. deploy the tomcat stack on the cluster.

   ```txt
   docker stack deploy -c stack.yaml tomcat-stack
   ```

4. check status of services and containers of tomcat-stack in the cluster with these two commands.

   ```txt
   docker stack services tomcat-stack
   ```

   ```txt
   docker stack ps tomcat-stack
   ```

5. profit.
