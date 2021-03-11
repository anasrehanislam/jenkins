Note: If in minikube jenkins not working give permisions to /data/jenkins

Freestyle Project Execute Shell:
1- Add freestyle project
2- In "Source Code Management" select git and add git repo alongside credentials
3- In "Build" section select "Execute Shell" option then Add below commands
echo "executing shell.."
docker build -t rehanislam/nginx:0.1 .
docker run -it -d --name nginxcontainer -p 8083:80 rehanislam/nginx:0.1

Add webhook:
Install ngrok
$ sudo snap install ngrok
Expose jenkins to the internet
$ ngrok http -host-header=localhost 8080 #Jenkins local URL
Add webhook on github
Set payload url http://bdd3bf8b8847.ngrok.io/github-webhook/
Select "just the push event"
Configure Jenkins project and select "GitHub hook trigger for GITScm polling" in "Build Triggers" section

Freestyle Project push dockerhub
1- Add freestyle project
2- In "Source Code Management" select git and add git repo alongside credentials
3- Inside jenkins container login to docker "docker login"
4- Install plugin "CloudBees Docker Build and Publish" plugin
5- Configure project again
6- In "Build" section select "Docker Build and Publish" option
7- Add credentials in the "Registry credentials" section
8- Add webhook again to build on push event
9. Go to "Build Trigger" section select option "GitHub hook trigger for GITScm polling"

Add pipeline Project:
1- Install "Docker Pipline" plugin
1- In "pipeline" section select "Git" option
2- Add Repository URL:https://github.com/anasrehanislam/jenkins.git and credentials
3- In "Script Path" add Jenkinsfile path.
4- Save and build