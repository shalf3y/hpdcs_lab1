# Високопродуктивні розподілені обчислювальні системи — лабораторна робота 1

**Савченко Михайло, Бондаренко Олена (КІ-31мп)**

**Task 1: Hello-world**
1. Installed docker and docker-compose
2. Opened terminal, executed `docker pull hello-world` to install hello-world package
3. Created `docker-compose.yaml`
4. Executed `docker-compose up`
<img width="1177" alt="Screenshot 2023-10-25 at 19 11 34" src="https://github.com/shalf3y/hpdcs_lab1/assets/122876241/4a9b8216-2280-485a-a4fa-6993bad2840c">
The container started up successfully. 

**Task 2: Lite-server**
1. Executed `docker pull node` to install node
2. Created `docker-compose.yaml`, our configuration sets up a Node.js container with lite-server, maps port 8080 on the host to port 8080 on the container, mounts the ./static directory on the host to /app/static in the container, sets the working directory, and runs the lite-server command.
3. Created static resources: created a directory named `static` in our project directory, added some static HTML to be served by lite-server.
4. Deployed container by running `docker-compose up` and tested.
<img width="1177" alt="Screenshot 2023-10-26 at 15 36 17" src="https://github.com/shalf3y/hpdcs_lab1/assets/122876241/0599639a-e594-4274-8458-0ee2bfeee207">
The page opens up successfully:
<img width="906" alt="Screenshot 2023-10-26 at 19 54 05" src="https://github.com/shalf3y/hpdcs_lab1/assets/122876241/8ad08930-4eb9-485f-a563-a06359b1debd">

**Task 3: JSON-server**
1. Created a new `docker-compose.yaml` file in our project directory. The configuration sets up a Node.js container with JSON-server, maps port 3000 on the host to port 3000 on the container, mounts the ./data directory on the host to /app/data in the container, sets the working directory, and runs JSON-server.
2. Created a data directory in the project directory and created a file named db.json with some sample JSON data.
3. Deployed the container with `docker-compose up` command and tested it by navigating to `http://localhost:3000/posts`
<img width="1177" alt="Screenshot 2023-10-26 at 20 07 40" src="https://github.com/shalf3y/hpdcs_lab1/assets/122876241/e0b8ba11-338d-4872-aae2-ed51214e48cd">
Tested successfully:
<img width="1059" alt="Screenshot 2023-10-26 at 20 08 12" src="https://github.com/shalf3y/hpdcs_lab1/assets/122876241/6d1cd611-dfee-403d-a5be-884d24b1a8f6">

**Task 4: Nginx + lite-server + JSON-server**
1. Pulled nginx by runnning `docker pull nginx`
2. Created docker-compose.yaml to set up three services: Nginx, lite-server, and JSON-server. Nginx listens on port 80 and forwards requests to the lite-server and JSON-server containers.
3. Created nginx directory inside project directory and created its configs: nginx.conf and default.conf. Our Nginx configuration listens on port 80 and forwards requests to either the static content (/) or to the lite-server (/lite-server/) and JSON-server (/json-server/) services.
4. Deployed containers running the following comand to scale it by 3:
```docker-compose up --scale lite-server=3 --scale json-server=3```

**Task 5: Postman**
1. Installed Postman to perform further testing of containers deployed in step 4.
2. Created a request collection.
3. Created three GET requests to test each service.
4. Tested successfully, all three services are working and the ports are being mapped correctly. Exported the collection to JSON. 

All environments and configuration files are available in separate directories for each task.
