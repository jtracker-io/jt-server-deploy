# Deploy JTracker Services using Docker Compose

Using Docker Compose is the easiest way to bring up all Tracker services. It also deploys the dependent `etcd` backend
and NGINX as reverse proxy.

## Prerequisites

Please follow Docker Documentation (https://docs.docker.com/) to install Docker and Docker Compose.

## Clone this repository

```
$ git clone https://github.com/jtracker-io/jt-server-deploy.git
```

## Fire up all JTracker Services
If you don't need to customize any settings, the following two commands will have all three
JTracker services up running.

```
$ cd jt-server-deploy
$ docker-compose up
```

If you run this on local computer, Swagger UI of the services will be available at the following URLs:
- JTracker Account Management Service: http://localhost:8001/api/jt-ams/v0.1/ui/
- JTracker Workflow Registration Service: http://localhost:8001/api/jt-wrs/v0.1/ui/
- JTracker Job Execution Scheduling Service: http://localhost:8001/api/jt-jess/v0.1/ui/

Otherwise, replace `localhost` with the IP of the server.

## Install and config JT-CLI to talk to the JTracker Services
Please follow instruction here to install JT-CLI: https://github.com/jtracker-io/jt-cli.

After installation of JT-CLI, you will need to config it so that it talks to the services you set up and run earlier.

Edit `.jtconfig` file under your home directory with the appropriate IP address.
```
ams_server: http://127.0.0.1:8001/api/jt-ams/v0.1
wrs_server: http://127.0.0.1:8001/api/jt-wrs/v0.1
jess_server: http://127.0.0.1:8001/api/jt-jess/v0.1
```
Please replace `127.0.0.1` with the correct IP of your server.

With that you should be able to create your own account using JT-CLI tool:
```
$ jt user signup -u user2
$ jt user login -u user2
```
You may use the pre-created user account `user1` if you prefer.

Note that authentication has not been implemented yet.

Now, you should be able to complete a quick tutorial using your own JTracker server.
Start from here: https://github.com/jtracker-io/jt-cli#register-a-jt-workflow-under-your-account
