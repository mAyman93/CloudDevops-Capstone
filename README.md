# CloudDevops-Capstone
This is the final project for Udacity cloud devops nanodegree. This piepline is applied on a simple html file

## Blue green Deployment
A Blue/Green deployment is a way of accomplishing a zero-downtime upgrade to an existing application. The “Blue” version is the currently running copy of the application and the “Green” version is the new version. Once the green version is ready, traffic is rerouted to the new version.

###### Basic Flow:

1- Start with already deployed containers (Deployment) and service.<br />
2- Deploy new deployment<br />
3- Issue a health check<br />
4- If health check passes, update load balancer and remove old deployment<br />
5- If health check fails, stop and send Slack alert
