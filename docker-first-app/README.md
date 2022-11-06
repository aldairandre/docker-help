# Introduction To Docker


## How To Run

### Install Dependencies
Access the ./api directory in your shell and run the command line:
```
npm install
```

With that we install the Node dependencies we need. I'm using Node 12.

### Building The Images

Access the project's root folder and build each image (MySQL, Node API and PHP):

```
docker build -t mysql-image -f api/db/Dockerfile .
```
```
docker build -t node-image -f api/Dockerfile .
```
```
docker build -t php-image -f website/Dockerfile .
```

### Running The Containers
In the root folder of the project, run one at a time:

```
docker run -d -v $(pwd)/api/db/data:/var/lib/mysql --rm --name mysql-container mysql-image
```
```

docker run -d -v $(pwd)/api:/home/node/app -p 9001:9001 --link mysql-container --rm --name node-container node-image
```
```
docker run -d -v "$(pwd)/website":/var/www/html -p 8888:80 --link node-container --rm --name php-container php-image
```

### Now Do Your Database:
```
docker exec -i mysql-container mysql -uroot -proot < api/db/script.sql
```