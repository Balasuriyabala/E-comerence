ON-PREM Kubernetes Deployment

k3 type kubernetes used and runtime security 

opensource tool: falco are used for runtime security

K3s:

Pods list:

<img width="536" height="160" alt="image" src="https://github.com/user-attachments/assets/830f9002-e985-4df6-bd30-605b74cf947b" />

SVC list:

<img width="660" height="143" alt="image" src="https://github.com/user-attachments/assets/65bb6fc0-f9dc-425b-80a7-ba127f80915f" />

Terminal:

<img width="653" height="245" alt="image" src="https://github.com/user-attachments/assets/b2a2918b-5374-4e5b-b042-be9e06f8318e" />

<img width="645" height="210" alt="image" src="https://github.com/user-attachments/assets/aa21f469-c1ad-440d-84be-bca01c9278ef" />

In the web console:

<img width="859" height="214" alt="image" src="https://github.com/user-attachments/assets/4cdb6424-430b-4cab-b595-f41ab5b5b658" />

Deploy the falco using helm chart:

helm repo add falcosecurity https://falcosecurity.github.io/charts

helm repo update

Check whether Helm is installed: helm version

helm install --replace falco --namespace falco --create-namespace --set tty=true falcosecurity/falco 

my case am using a k3s method so check the helm is connected to cluster it not run the following command 

echo $KUBECONFIG - if its return empty we need to set itup 

export KUBECONFIG=/etc/rancher/k3s/k3s.yaml

Test: helm list

kubectl get pods -n falco

<img width="878" height="199" alt="image" src="https://github.com/user-attachments/assets/1b36c284-b75c-49b0-b389-1559c31c1cd2" /> 

after setting a rule load it to falco:

helm upgrade --namespace falco falco falcosecurity/falco --set tty=true -f falco_custom_rules_cm.yaml 

Falco pod(s) might need a few seconds to restart. Wait until they are ready

Install Falcosidekick and Falcosidekick-UI in your test cluster:

helm upgrade --namespace falco falco falcosecurity/falco -f falco_custom_rules_cm.yaml --set falcosidekick.enabled=true --set falcosidekick.webui.enabled=true 

kubectl -n falco get svc

Run in the background from the current shell

kubectl -n falco port-forward --address 0.0.0.0 svc/falco-falcosidekick-ui 2802:2802 &

admin & admin for login

case:1 it detects whensomeone start asn interactive shell 

<img width="924" height="215" alt="image" src="https://github.com/user-attachments/assets/fee5d211-ac37-4321-9a54-2af146347149" />

I get into pod and written a main.tf file

<img width="733" height="123" alt="image" src="https://github.com/user-attachments/assets/90412825-b5aa-48e4-b212-484f2ef012fd" />

<img width="945" height="138" alt="image" src="https://github.com/user-attachments/assets/d5a353ac-d063-42eb-b4e6-893dcb3f38f3" />


<img width="937" height="403" alt="image" src="https://github.com/user-attachments/assets/7a18381e-6f76-47ba-b29a-537e449259bc" />











