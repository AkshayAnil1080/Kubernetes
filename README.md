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


k8-4 -  12.	Docker container in LAN 
	13. 	Replication Controller
	14.     EXPOSE CONTAINERS TO PUBLIC WORLD
	15. 	CREATE RPLICAS

k8-5 -  16.	Types of LoadBalancing(LB) - a. Cluster IP - b. NodePort - c. External LB
	1. Create a LB code
	2. Use of LABELS
	3. Regisetr newly launched Pod under ENDPOINTS OF LB.
	4. Verifying CLuster IP Load balancing.
	5. Exposing to Public World: NodePort Load balancing
	6. Verifying NodePort Load balancing via CLI and GUI both.


k8-6 - 	17.	DEPLOY MULTINODE ARCHITECHTUTE IN K8
	1.launching one pod in k8 and configuring Wordpress image as fronted.
	2.launching another pod in K8 and configuring mysql database as backend.
	3.Exposing the fronthend(NODE PORT in K8) server for public client.
	4.keeping another OS isolated as the best secuty is avaoid the networking with public world.
	5.Concept of ENVIRONMENT VARIABLES also known as Shell Variables.
	6.login into the pod of database via CLI and then login in mysql to view and edit the tables.



k8-7 - 	18.	Launching the DB mySQL via yaml code in KUBERNETES-
	19.	SECRET SERVICE OF K8 via yaml-
			<i>Encoding the confidential Info of DB, like root_passwrod and username, as to use mysql image we have pass four info 
			(MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER, MYSQL_PASSWORD) as Environment Variables.</i>
	20.	Extracting the encoded password of secret via CLI –
			<i>K8’s master server only understands YAML, so pod launched via CLI even first get converted to YAML then passed in to K8 for executing.
			So, exposing this file will get me the encoded password too and can decode it by base64 conversion.</i>
	21.	Create a secret key via CLI
			<i>Exploring the help command to get the usage of SECERET in K8 via CLI.</i>

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

21. kubectl get pods -L <labelKeyName>
22. kubectl get rc   
23. kubectl describe rc <rcName>
24. kubectl expose rc <rcName>  --port=80  --type=NodePort
25. kubectl get services  - loadbalancing perfomed by K8 - clusterIP, NodePort, External LoadBalancer
26. ifconfig | less 
27. curl http://IP:Port

28. kubectl get svc -    status of services
29. kubectl get svc <podName>
30. kubectl describe svc <podName>

31. kubectl run mydb –image=mysql:5.7  					
32. kubectl logs mydb							
33. kubectl exec -it myos1 -- bash						
34. x=4  echo$x											
35. vi /root/.bashrc							
36. kubectl run myos1 --image=vimal13/apache-webserver-php --env=x=10  
37. kubectl run mydb --image=mysql:5.7 --env=MYSQL_ROOT_PASSWORD=redhat --env=MYSQL_DATABASE=wpdb --env=MYSQL_USER=akshay --env=MYSQL_PASSWORD=anil
38. mysql -u <username> -p<password> 					 
39. SQL commands
    show databases;
    use <databaseName>
    show tables;
40. kubectl run mywp –image=wordpress:5.1.1-php7.3-apache    		 
  
41. kubectl get secrets   						
42. kubectl get pods <podanme> -o yaml.					
43. kubectl get secret mysecret -o yaml					
44. kubectl create -h							
45. kubectl create secret generic mys  --from-literal=key=value	

FAQ:
K8-1
👉 What is Kubernetes?
✔1. it is a tool used for Container management
👉 What are the benefits of using Kubernetes?
✔2. autoscaling: automatic launch and shutdown of containers as per the traffic.
Multi tenancing: capability to manage multiple host.
👉 On which architecture does Kubernetes work?
✔3.it works on the architecture of Pods.
👉 What is a multinode cluster and single-node cluster in Kubernetes?
✔4.multi node cluster – one master(controller) and multiple workers(POD)
Single node – one system behaving as master and worker both.
👉 What do you mean by a pod in Kubernetes?
✔5. the container in DE is known as Pods in K8.


K8-2
👉what is minikube?
✔6  Minikube is a tool help in installing K8.
👉How to install minikube and kubectl ?
✔7 minikube.exe start --driver=virtualbox --kubernetes-version=v1.20.0
Open command as admin - curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.20.0/bin/windows/amd64/kubectl.exe - download kubectl
👉How to run any pod through kubectl ?
✔8  give the pod name and the image name.
kubectl.exe run myweb1 --image=vimal13/apache-webserver-php
👉What do you mean by exposing the pod?
✔9 making the container open to public world, i.e anyone with the url can access the server.

👉How to expose the pod?
✔10 kubectl.exe expose deployments <podname>  --port=80  --type=NodePort
👉 Difference between pod and container?
✔11 the os launched over docker is container and the container launched by K8 is pod.
👉 Difference between pod and deployment?
✔12 if the pod is launched by the using just the image, once deleted, it will delete the pod and will not relaunch automatically.
If the pod is launched through the deployment controller program, once deleted, it will delete and relaunch the pod simultaneously.

K8-3
👉What is single node cluster?
✔13 Single node – one system behaving as master and worker both.
👉What is deployment controller 🎮?
✔14. DEPLOYEMNT CONTROLLER PROGRAM monitors the management of pod. As the pod goes down, it will launch it again
👉What is fail over?
✔15. it means, if any pod goes down , K8 launches the exact copy of it.



👉What is kube API/API server?
✔ 16.the program through which the client interact to Kubernetes server or master.
👉What are ways to send request to kubernete Server?
✔17. there are two ways : via code and CLI.
👉What is YAML language.How to write code in YAML language?
✔18. yaml is a markup language which use key value pair and involves indentation. K8 scripts are written in yaml language. and execute it via command : kubectl create -f <filename>
👉What is kubelet program?
✔19.kubelet is a program used by k8 to launch a container.
👉What is kubernete resources?
✔20. the keywords like pod , deploy in K8 are known as resources.
👉 Use of get and describe command?
✔21.kubectl.exe get deployments- total deployed pods by deployment controller program in K8
kubectl.exe get pods- total number of running pods.
kubectl.exe describe pods- gives the every details of pods.
👉 What is use of spec and kind keyword?
✔22. kind: the keyword use to specify the pod.
Spec:  the specification of pod -> name of the container and the images used.

K8-4
👉 What is RC ?
✔23. RC is a replication controller program which manages the monitoring of container in case of failover.
👉 What is replica?
✔24. Replica is container which is the exact copy made from another container.
👉 difference between create and apply?
✔25. If a particular yml file has already run once in K8 , and requirement re run the same program with some minor changes, then create keyword is not applicable, one has to apply keyword.
kubectl create -f rc.yml
kubectl apply -f rc.yml
👉 command to see replication controller?
✔26. kubectl get rc
👉 What is labels ?
✔27. Management of container with the help of its IP is very dynamic as it changes on every restart, so instead we use a tag name or the label which remain static until the container is deleted. The labels are written is key value pair.


K8-5
👉 How and where is Reverse Proxy used in Kubernetes?
✔28 the program running to serve on behalf of another is SERVER PROXY. 
It has a feature Load balancer which balances the load and distribute the load to multiple same webserver hosted. 
Reverse proxy is the process when the hosted server gives the response back to fronend(LB) as well as the recreation of request of client, it prevents the direct interaction between client and the backend server 
👉 What are the different types of services in Kubernetes?
✔29.  Cluster IP: the connectivity among the pods.
Node port: it enables the connection between the public world and the private network of pods(container in docker) of K8. 
External Load Balancer : if using an external load balancer like using EKS of AWS to manage the connectivity between pods and the public world(Internet).
👉 What is the importance of labels?
✔30. Management of container with the help of its IP is very dynamic as it changes on every restart, so instead we use a tag name or the label which remain static until the container is deleted. The labels are written is key value pair.
👉 How does the NodePort service work?
✔31. it is a load balancing service which enable the connection between the public world and the private network of pods(container in docker) of K8.
👉 What is the difference between port, target port and Nodeport?
✔32. port is unique number on which a program runs.
When Program running inside container uses a port number, it is target port.
Node port is the port number of base OS which has the pod running in it


