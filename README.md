# CST8915 - Lab 7: Kubernetes Basics


## Demo Video
YouTube Link: [Video](https://youtu.be/ub__G6QeprM)]

## RabbitMQ Configuration Analysis
  
### Is RabbitMQ Stateful or Stateless?
RabbitMQ is a stateful because it stores information and preserves data. Statless applications do not store any data or messages.

### Problems Without Persistent Storage
The problem is whenever a pod is deleted and is replaced (which happens a lot in Kubernetes) all the information is lost. The new container will start without the previous container stored data. This can disrupt communications between the services. 

### What Happens When the RabbitMQ Pod Is Deleted?
When I deleted the pod which was then automatically replaced due to the K8 Deployment, the queue in RabbitMQ portal was erased. It showed a '...no queues..." display.

### Potential Solutions
According to the official Kubernetes website, Kubernetes can be created with persistent volumed called PersistentVolume (PV) and PersistentVolumeClaim (PVC).  This allows RabbitMQ to store its data outside the container's temporary filesystem so that it can survive Pod replacement.

### Would Azure Service Bus Solve These Issues?
It can be used to solve this issue because Azure Service Bus is a managed system under Azure, Azure manages the underlying infrastructure and message storage. It would replace the need to use PV and PVC's. 

### References: 
- [Kubernetes Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) 
