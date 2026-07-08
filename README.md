# Two Applications in One Node (Kind Kubernetes)

## Step 1: Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
```

---

## Step 2: Install kubectl

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

---

## Step 3: Install Kind

```bash
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.32.0/kind-linux-amd64
chmod +x kind
sudo mv kind /usr/local/bin/
```

---

## Step 4: Create Cluster

```bash
kind create cluster --name kind-demo --config config.yml
```

---

## Step 5: Create Namespace

```bash
kubectl create namespace nginx-2
```

---

## Step 6: Create Deployment

```bash
kubectl apply -f deployment.yml
```

---

## Step 7: Create Service

```bash
kubectl apply -f service.yml
```

---

## Step 8: Verify

```bash
kubectl get deployment -n nginx-2
kubectl get pods -n nginx-2
kubectl get svc -n nginx-2
```

---

## Step 9: Access Application

Open:

* http://localhost:8080
* http://localhost:8081
