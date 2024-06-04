apiVersion: apps/v1

This code specifies that the configuration follows the Deployment API version 1 within the apps API group of Kubernetes. Deployments are a core Kubernetes construct for managing the lifecycle of replicated pods.
kind: Deployment

This code declares that the type of Kubernetes resource being defined is a Deployment.
metadata:

This section provides metadata about the deployment, including its name.
name: client
This assigns the name "client" to the deployment. This name will be used to identify and manage the deployment within Kubernetes.
spec:

This section defines the desired state of the deployment, specifying how Kubernetes should manage the pods.
selector:
This section defines how pods are selected to be part of this deployment.
matchLabels:
app: client
This part uses a label selector to match pods that have a label named "app" with the value "client". Pods with this label will be considered part of this deployment and managed by it.
template:
This section defines the template used to create pods for this deployment. Any pods created by this deployment will be based on this template.
metadata:
labels:
app: client
This again sets the label "app" with the value "client" on the pods created by this deployment. This ensures that the selector defined earlier can identify these pods.
spec:
containers:
This section defines the container(s) that will be included in the pods created by this deployment.
name: client
This assigns the name "client" to the container within the pod.
image: vanessamayama/client:v1.0
This specifies the Docker image to be used for the container. The image comes from a repository named "vanessamayama" and uses the tag "v1.0".
resources:
This section defines resource limits for the container.
limits:
memory: "512Mi"
This sets a memory limit of 512 Megabytes (Mi) for the container.
cpu: "500m"
This sets a CPU limit of 500 millicores (m) for the container.
ports:
This section defines the ports that the container exposes.
containerPort: 3000
This specifies that the container exposes a port mapped to port 3000 within the pod.
In summary, this YAML configuration defines a Kubernetes deployment named "client" that will create pods running the container image "vanessamayama/client:v1.0". The pods will have a label "app: client" and resource limits set for memory and CPU. The container within the pods will expose a port mapped to port 3000. When you deploy this configuration in Kubernetes, it will create and manage pods based on this template, ensuring a continuously running instance of your "client" application.
This Code is also replicated for the backend.





API Version and Kind:

apiVersion: v1

kind: Service

These lines specify that the configuration follows the Service API version 1 within the core API group of Kubernetes. Services are a fundamental concept in Kubernetes for exposing applications running in pods.

2. Metadata:

metadata:

name: client
This section provides metadata about the service, including its name. Here, it's assigned the name "client". This name will be used to identify and manage the service within Kubernetes.

3. Spec:

spec:

This section defines the desired state of the service, specifying how Kubernetes should expose the pods associated with it.

selector:

app: client
This section defines how to select pods that will be part of this service. It uses a label selector to match pods that have a label named "app" with the value "client". Pods with this label will be considered manageable by this service.

ports:

port: 80
targetPort: 3000
This section defines how external traffic will be routed to the pods.

port: 80 specifies that incoming traffic will be received by the service on port 80 (the standard HTTP port).
targetPort: 3000 specifies that this incoming traffic on port 80 will be forwarded to port 3000 within the selected pods (which presumably is where the application listens for requests).
type: LoadBalancer

This crucial part defines the service type. Here, it's set to LoadBalancer. This instructs Kubernetes to create an external load balancer that will route incoming traffic on port 80 to one of the healthy pods that match the selector (app: client). The load balancer will typically provide a single, public IP address for accessing the service.

In essence, this service acts as a virtual gateway for external clients. Clients can access the application running in the pods by sending requests to the service's external IP address on port 80. Kubernetes will then distribute the traffic across the available healthy pods that have the label "app: client" and expose their service on port 3000.

This configuration, when used in conjunction with the deployment you provided earlier (assuming they both have the label "app: client"), creates a robust deployment scenario:

The deployment ensures a continuously running instance of your "client" application in pods.
The service provides a stable and discoverable way to access the application from outside the Kubernetes cluster using a single IP address.

This is also replicated for the backend
