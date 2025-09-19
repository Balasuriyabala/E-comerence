 # E-comerence 

Stage-1 Docker with Jenkins

Deployed a code and the container is up & running  = ok


stage-2 the aplicatio nexposing via port no:3000 now we need to used nginx 

exposed the application using a nginx = ok

nginx sites-available:

server {
    listen 80;
     server_name <IP> ;   # use your domain name if you have one, else keep _

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}



Q) new build confilt with old container already existing confilit? 

 Ans: Follow any deployment stargies




