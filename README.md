Pithos Quickstart
====================

Bases
This builds a Docker image for [Pithos](https://github.com/exoscale/pithos) and it also provides Kubernetes pods, replication controller and service to run Pithos in Kubernetes.

## Launching Pithos S3 object store

[Pithos](http://pithos.io) is a daemon which "provides an S3 compatible frontend to a cassandra cluster". So if we run Pithos in our Kubernetes cluster and point it to our running Cassandra cluster we can expose an S3 compatible interface.

To that end I created a Docker image for Pithos _runseb/pithos_ on Docker hub. Its an automated build so you can check out the Dockerfile there. The image contains the default configuration file. You will want to change it to edit your access keys and bucket stores definitions. I launch Pithos as a Kubernetes replication controller and expose a service with an external load balancer created on Google compute engine. The Cassandra service that we launched earlier allows Pithos to find Cassandra using DNS resolution. 

