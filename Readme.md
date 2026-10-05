###Docker Compose
Here is a minimal Docker Compose configuration sample project alongside the most essential commands to manage it.
1. Sample Project Files
Create a directory for your project, then add the following two files into it:
index.html (A basic landing page)
html
<!DOCTYPE html>
<html>
<body>
    <h1>Hello from Docker Compose!</h1>
</body>
</html>
Use code with caution.
compose.yaml (The blueprint for your multi-container environment)
yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./index.html:/usr/share/nginx/html/index.html:ro

  database:
    image: postgres:15-alpine
    environment:
      POSTGRES_DB: my_database
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secret_password
Use code with caution.
________________________________________
2. Essential Docker Compose Commands
Run these commands in the terminal from inside the project directory containing your compose.yaml file:
Lifecycle Management
•	docker compose up -d – Starts your entire application stack in the background (detached mode). [1, 2]
•	docker compose down – Stops all containers, stops the virtual network, and cleans up the project footprint. [1]
•	docker compose down -v – Stops containers and entirely wipes out any declared persistent volumes. [1, 2]
•	docker compose stop – Pauses your containers without deleting the network configuration or data. [1]
•	docker compose start – Resumes your already existing, stopped containers. [1]
Inspection & Debugging
•	docker compose ps – Shows the current operational status and port mappings of all services in the project. [1, 2]
•	docker compose logs -f – Streams live terminal outputs and error logs directly from all running containers. [1, 2]
•	docker compose config – Validates your YAML syntax configuration and resolves active environment variables. [1, 2]
Executing Commands
•	docker compose exec web sh – Opens an interactive shell inside your running web container.
•	docker compose run --rm web nginx -v – Runs a temporary one-off command inside a new instance of your service, then instantly removes it. 

