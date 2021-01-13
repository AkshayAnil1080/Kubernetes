# demos
k8-1 - INTRODUCTION AND NEED.

k8-2 -  1.	Install k8
	2.	Install kubectl.exe
	3.	Installing one image in pod
	4.	Deletion of the pod
	5.	DEPLOYEMNT CONTROLLER PROGRAM
	6.	Check every step of pod management
	7.	GUI interface of Minikube
	8.	Exposing the IP of pod to outside world.
	9.	Creating replica of a pod
	10.	Checking deletion and automatic relaunching of Pod

k8-3 -  11.     Lanunching pod via code.


k8-4 -  12.	Replication Controller

k8-5 -  13.	Types of LoadBalancing(LB) - a. Cluster IP - b. NodePort - c. External LB

# Commands till yet:

1. cd "C:\Program Files\Kubernetes\Minikube"
2. minikube.exe start --driver=virtualbox --kubernetes-version=v1.20.0
3. minikube status
4. curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.20.0/bin/windows/amd64/kubectl.exe - download kubectl
5. kubectl.exe get pods  
6. kubectl.exe run myweb1 --image=vimal13/apache-webserver-php
7. kubectl.exe delete pod myweb1
8. kubectl.exe create deployment myweb1 --image=vimal13/apache-webserver-php
9. kubectl delete -n default deployment myweb1
10. kubectl.exe describe pods
11. minikube dashboard
12. minikube.exe start/stop
13. kubectl.exe expose deployments myweb1  --port=80  --type=NodePort - expose the pod to public -PATing
14. minikube service myweb1 --url
15. kubectl.exe scale deployment myweb1 --replicas=4
16. kubectl.exe get deployments
17. minikube delete all --all

18. kubectl.exe delete all --all
19. in vm : docker ps |  grep vimal13
20. kubectl.exe create -f pod.yml  