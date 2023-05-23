# posts
Simple React Client with several Node.js Microservices as Docker images running within a Kubernetes Cluster

## Services

Client React-Application running locally on post.com
Posts Service which handles new Posts.
Comment Service which handles new Comments.
Moderation Service which checks new Comments for forbidden content (in this case, whether a comment contains the word "orange").
Query Service which bundles Post and Comments
Event-Bus Service which receives and distributes all events emitted by other services (just like kafka but very simple).

## Dev-Setup

Docker needs to be installed and kubernetes must be enabled.

The Projekt uses Skaffold in order to update docker images and apply those changes to the kubernetes pods, which are running the changed services.
Install Skaffold and run the command "skaffold dev" to start all kubernetes pods

The routing is done by an [ingress-nginx controller](https://kubernetes.github.io/ingress-nginx/) which must be installed as well.

To run the client locally, you have to route all requests in your browser to "posts.com" to your localhost 127.0.0.1.
Therefore you have to change your local /etc/hosts file.
Just add "posts.com 127.0.0.1" to the file.
