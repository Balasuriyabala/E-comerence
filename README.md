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


# Infrastructure:

Frontend & Backend code are deployed via Docker container, where mongodb is installed in host machine 

application exposed through nginx

Problem faced:

1. While choosing a open soucrce project for the frontend and backend connection no .env file?

Ans: Install mongodb in vm and do configuration for connection and update the .env file with mongodb-url, port-no, jwt-key

2. Sigin or signup faced error : CONNECTION REFUSED we can see from inpecting page 

why this error:

Inside backend container, localhost = backend container itself, not your host.

To reach MongoDB on your host, you must use the host machine IP, not localhost.

Ans: Update src/api/index.js from local host to machine ip



