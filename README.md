# devops-task

# 1. Docker Task
## Summary:-
Application consist of frontend and backend, for frontend i have used flask and for backend database i have postgresql database. Basically this application supports GET and POST request. We can do PUT request on url http://localhost:80/items with content and title body once we put this json content, we can easily access these json content from browser and in background these data stores in our postgresql which is running locally. 

We can also do GET request to see all the PUT itmes.

## Files Content:-
1. requirements.txt --> contains the dependencies to be installed 
2. app.py --> Application file
3. Dockerfile --> Containerize the Application
4. docker-compose --> To run both frontend and backend application.

## Commands:-
1. pip install -r requirements.txt
2. docker-compose up -d
3. access application on http://localhost/items/<id>


# 2. Kubenretes Task
## Summary:- 
We have two namespace first is backand where we have deployed our mongo db database and second is frontend where we have deployed web application. Frontend applications needs to communicate with database so for that communication we have used here the fqdn concept so for communication of frontend with database we use SERVICE_NAME.NS. Frontend application is exposed publically by LoadBalancer so that everyone can access from outside world and database application is in private where we have used ClusterIP. 

We have used HPA for frontend pod, autoscaling will based on CPU utilisation. To increase the load of CPU utilisation we have deployed one job ,the role of this job is to send hundreds of concurrent visitors on your website at once to check how it will perform under pressure and how much availability your server can provide.

## Files Content:-
1. ns.yaml --> Create frontend and backend ns
2. db.yaml --> Deploy the mongodb application
3. frontend.yaml --> Deploy the frontend web application
4. hpa.yaml --> HPA on frontend application
5. job.yaml --> Siege HTTP load test tool to increase the CPU load

## Commands:-
1. kubectl apply -f ns.yaml
2. kubectl apply -f db.yaml
3. kubectl apply -f frontend.yaml
4. kubectl apply -f hpa.yaml
5. kubectl apply -f job.yaml
