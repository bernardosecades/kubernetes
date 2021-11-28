# Kubernetes (with minikube)

Learning kubernetes with minikube.

## Environment

- Install a Hypervisor (virtual machine):
  - VirtualBox
  - KVM
  - ...

- Install minikube:
  - https://minikube.sigs.k8s.io/docs/start/
- Install kubectl
  - https://kubernetes.io/docs/tasks/tools/


## Docker image to create containers

We are using bernardosecades/hello-dude docker image to test (it is web server with endpoint /hello)
- https://hub.docker.com/r/bernardosecades/hello-dude

You can see the implementation here: https://github.com/bernardosecades/hello-dude

## Create alias for minikube kubectl command

Create alias for minikube in your bash profile:

```
alias mk="minikube kubectl --"
```

## Create namespace "testing" in our minikube cluster

```
mk apply -f 00-namespace.yml
```

And permanently save the namespace for all subsequent kubectl commands in that context:

```
mk config set-context --current --namespace=testing
```

Validate it
```
mk config view --minify | grep namespace:
```

Examples: 

### [00-namespace.yml](00-namespace.yml)

Create namespace:

```
mk apply -f 00-namespace.yml
```

Check if namespaces were created:

```
mk get namespaces
```

### [01-pod.yml](01-pod.yml)

Create a pod:

```
mk apply -f 01-pod.yml
```

Check if namespaces were created:

```
mk get pod -n testing
```

(you can skip -n testing because we have testing namespace by default for current context)

## TODO

organize in folders and each folder contains README file to explain the use case.

