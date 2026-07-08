Step 1: Install Docker

sudo apt update
sudo apt install docker.io -y

Step 2: Install kubectl

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/

Step 3: Install Kind

[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.32.0/kind-linux-amd64
chmod +x kind
sudo mv kind /usr/local/bin/

Step 4: Create cluster

kind create cluster --name kind-demo --config config.yml

Step 5: Create Namespace

kubectl create namespace nginx-2

Step 6: create Deployment

kubectl apply -f deployment.yml

Step 7: create Service

kubectl apply -f service.yml

Step 8: Verify

kubectl get deployment -n nginx-2
kubectl get pods -n nginx-2
kubectl get svc -n nginx-2

Step 9: Access Application
Open:

http://localhost:8080
        OR
http://localhost:8081
