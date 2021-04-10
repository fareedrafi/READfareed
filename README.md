# READfareed
Run the app in Kubernetes
The folder k8s-specifications contains the yaml specifications of the Voting App's services.

First create the vote namespace

$ kubectl create namespace vote
Run the following command to create the deployments and services objects:

$ kubectl create -f k8s-specifications/
deployment "db" created
service "db" created
deployment "redis" created
service "redis" created
deployment "result" created
service "result" created
deployment "vote" created
service "vote" created
deployment "worker" created
The vote interface is then available on port 31000 on each host of the cluster, the result one is available on port 31001.

Architecture
Architecture diagram

A front-end web app in Python or ASP.NET Core which lets you vote between two options
A Redis or NATS queue which collects new votes
A .NET Core, Java or .NET Core 2.1 worker which consumes votes and stores them in…
A Postgres or TiDB database backed by a Docker volume
A Node.js or ASP.NET Core SignalR webapp which shows the results of the voting in real time
Notes
The voting application only accepts one vote per client. It does not register votes if a vote has already been submitted from a client.

This isn't an example of a properly architected perfectly designed distributed app... it's just a simple example of the various types of pieces and languages you might see (queues, persistent data, etc), and how to deal with them in Docker at a basic level.
