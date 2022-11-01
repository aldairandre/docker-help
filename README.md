
# First Steps with Docker 

## What is Docker?

**init docker server in wls2**

``service docker start``


**Start a mongo server instance**

`docker run -d --name mongodb -e MONGO_INITDB_ROOT_USER=admin -e MONGO_INITDB_PASSWORD=123 -p 27017:27017 mongo`
<p>
  Where some-mongo is the name you want to assign to your container and tag is the tag specifying the MongoDB version you want.
</p>


**Container shell access and viewing MongoDB logs**
<p>
The docker exec command allows you to run commands inside a Docker container. The following command line will give you a bash shell inside your mongo container
</p>


`docker exec -it mongodb mongosh`
