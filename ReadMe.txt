1- Add freestyle project
2- In "Source Code Management" select git and add git repo alongside credentials
3- In "Build" section select "Execute Shell" option then Add below commands
echo "executing shell.."
docker build -t rehanislam/nginx:0.1 .
docker run -it -d --name nginxcontainer -p 8083:80 rehanislam/nginx:0.1


To push Image on dockerhub
1- Install plugin
CloudBees Docker Build and Publish plugin
2-Configure project again
3- In "Build" section select "Docker Build and Publish" option
4- Add credentials in the "Registry credentials" section
5. In the "Build Trigger" section check option "GitHub hook trigger for GITScm polling"