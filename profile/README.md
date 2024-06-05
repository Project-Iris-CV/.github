# Intelligent Recognition and Integrated Surveillance
Integrated Recognition Intelligent Surveillance (IRIS) AI technology for object detection, with a primary focus on monitoring equipment states (On/Off). By analyzing the frequency and duration of equipment usage, IRIS assists Lab Supervisors with automated data gathering and real-time monitoring capabilities

# Installation Guide
## Downloading the source code
IRIS software is comprised of three main repositories: the service, backend, and frontend. To download the software, execute the following commands:

```bash
# clone the frontend repository
git clone https://github.com/Project-Iris-CV/IRIS-FRONTEND.git

# clone the backend repository
git clone https://github.com/Project-Iris-CV/IRIS-BACKEND.git

# clone the service repository
git clone https://github.com/Project-Iris-CV/iris-surveillance-service.git
```

## Setting up the environment
### Setup for frontend
Before launching the frontend, a `.env` file must be created containing the URL of the API endpoint of the backend. The `.env` file follows this format (In this example, the api endpoint `http://localhost:8080/api` was used.):

```
# .env for iris-frontend
VITE_API_URL="http://localhost:8080/api"
```

### Setup for backend
Setting up the backend involves configuring values for the `.env` file and using special arguments in the iris.py main file. The `.env` file follows this format:
```
IRIS_BACKEND_IP='0.0.0.0'
IRIS_BACKEND_PORT=8080
DATABASE_PATH='./app/db'
SALT='12345678'
SERVICE_URI='http://localhost:8081'
GMAIL_USERNAME='...'
GMAIL_PASSWORD='...'
```

These default values will be used on the backend server, but they can be modified as needed, especially when the current port is in use. The `SERVICE_URI` must match the URL of the service, which will be detailed later (`IP` and `PORT` assigned in the iris-service repository).


After initializing the `.env` for the backend, execute the following command to install the required modules and initialize the database:
```bash
pip3 install -r requirements.txt
python3 iris.py --initialize-db
```

### Setup for Service
To setup the service repository, kindly follow the steps:
1. Install the required modules through command:
   ```
   pip install -r requirements.txt
   ```

2. Initialize and update submodules using the following git commands (this will install another git repository dependency yolov5 which will be used for Computer Vision):
   ```
   git submodule init
   git submodule update
   ```
3. Create a .env file in the root directory of the service repository with the following format:
   ```
   SQLITE3_DB=db/data.db
   MONGO_URI=
   IMAGE_SNAPSHOT_DIR=public/images/snapshots
   DISABLE_STREAMS=false
   ```
4. Create the folder public/images/snapshots if it doesn't already exist.
5. Execute the `init.py` command to initialize the service database: `python init.py`
