# Intelligent Recognition and Integrated Surveillance
Integrated Recognition Intelligent Surveillance (IRIS) AI technology for object detection, with a primary focus on monitoring equipment states (On/Off). By analyzing the frequency and duration of equipment usage, IRIS assists Lab Supervisors with automated data gathering and real-time monitoring capabilities

# Software Installation and Setup
## Downloading the source code
IRIS Software has three (3) main repositories which includes the service, backend, and frontend. For downloading the software, the user can execute the following commands:

```bash
# clone the frontend repository
git clone https://github.com/Project-Iris-CV/IRIS-FRONTEND.git

# clone the backend repository
git clone https://github.com/Project-Iris-CV/IRIS-BACKEND.git

# clone the service repository
git clone https://github.com/Project-Iris-CV/iris-surveillance-service.git
```

## Setting up the environment
For setting up the software, initial setup for the downloaded repositories will be done, the setup includes `.env` modifcation and running of commands for initializing database and special values.

### Setup for frontend
Before firing up the frontend a `.env` must be created which will contain the url of the API endpoint of the backend. The `.env` has the following format (where in this example we use the API endpoint `http://localhost:8080/api` for backend URL):

```
# .env for iris-frontend
VITE_API_URL="http://localhost:8080/api"
```

### Setup for backend
The setup for backend includes setting up values for `.env` file and use of special arguments in `iris.py` main file. The `.env` has the following format:
```
IRIS_BACKEND_IP='0.0.0.0'
IRIS_BACKEND_PORT=8080
DATABASE_PATH='./app/db'
SALT='12345678'
SERVICE_URI='http://localhost:8081'
GMAIL_USERNAME='...'
GMAIL_PASSWORD='...'
```

By default, these values will be used on the backend server, but these values can be changed (especially for the case where the current `PORT` is being used). The `SERVICE_URI` must have the same URL as the service which will be shown later (`IP` and `PORT` assigned in the `iris-service` repository).

After initializing the `.env` for backend, the following command must be executed in order to initialize the database for backend:
```bash
python3 iris.py --initialize-db
```
