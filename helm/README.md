These are the steps to create a MySQL instance inside Kubernetes

# 0. Go to mysql directory inside helm
cd helm/mysql

# 1. Create 'prd' namespace
kubectl create -f namespace-prd.yaml

# 2. Create a storage class
kubectl -n prd apply -f sc-mysql.yaml

# 3. Create the persistent volume
kubectl -n prd apply -f pv-mysql.yaml

# 4. Install MySQL Helm Chart
helm install --namespace prd prd-mysql .

# 5. For subsequent release, run helm upgrade
helm upgrade --namespace prd prd-mysql .
