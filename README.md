# E-comerence 

This is the OpenSource repo link: https://github.com/rishavchanda/Ecomerce-website.git

Front-end Deployment 
Project Setup using below tools:
1. Git
2. Jenkins
3. Docker

Step-1 : Install Git in the Ubuntu server

Step-2 : Jenkins Server Setup in Ubuntu VM:
follow the link to setup the jenkins: https://www.jenkins.io/doc/book/installing/linux/#debianubuntu

Step-3 : Docker 
Install Docker on server refer offical documentation
from client folder we have wriiten the Multi-stage Docker file to reduce the size of the image

Step-4 : Create Jenkins pipeline Job
pipeline scripted attached in the repo 

Step-5 : To known
If you are using a react for front-end how to react version?
Ans: Pacakage.json file find  
     {  "react": "^18.2.0",
    "react-dom": "^18.2.0",}

Stage-1 Docker with Jenkins

Deployed a code and the container is up & running

stage-2 the aplicatio nexposing via port no:3000 now we need to used nginx


