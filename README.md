# CI/CD Pipeline using Nginx, Kubernetes, and Ansible

Containerzied application using nginx, kubernetes & ansible.

## Prerequisites

*   [Docker](https://docs.docker.com/get-started/get-docker/)
*   [Minikube](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download)
*   [kubectl](https://kubernetes.io/docs/tasks/tools/)
*   [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)


## 1. Clone repository
```bash
    git clone git@github.com:mmellblom/ci-cd-devops3.git
``` 
    
    

## 2. Deployment
```bash
    minikube start

    kubectl apply -f nginx-deployment.yml

    kubectl get pods
    kubectl get deployments

    minikube service nginx-service --url
```


## 3. Updating the Application
 ```bash
    ansible-playbook deploy-playbook.yml --extra-vars "image_tag=v1.0.0" # Replace v1.0.0 with new tag
```

## 4. Verification
```bash
    kubectl rollout status deployment/nginx-deployment

    minikube service nginx-service --url

    minikube dashboard
    kubectl get pods
```

## 5. Cleanup
```bash
    minikube stop
    minikube delete --all --purge # Deletes all images and volumes
```