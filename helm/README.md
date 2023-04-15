These are the steps to create a MySQL instance inside Kubernetes

# 0. Go to mysql directory inside helm
``cd helm/mysql``

# 1. Create 'prd' namespace
``kubectl create -f namespace-prd.yaml``

# 2. Create a storage class
``kubectl -n prd apply -f sc-mysql.yaml``

# 3. Create the persistent volume
``kubectl -n prd apply -f pv-mysql.yaml``

# 4. Install MySQL Helm Chart
``helm install --namespace prd prd-mysql .``

# 5. For subsequent releases, run helm upgrade
``helm upgrade --namespace prd prd-mysql .``

# --------------------------------------------------------------------------
In helm directory, do these steps to install Nginx PHP-FPM inside Kubernetes
# 6. Create the app (Nginx-PHP) storage class
``kubectl -n prd apply -f sc-app.yaml``

# 7. Create the persistent volume to store app data
``kubectl -n prd apply -f pv-app.yaml``

# 8. Install PHP-FPM Helm Chart
``helm install --namespace prd prd-php ./php``

# 9. Install Nginx Helm Chart
``helm install --namespace prd prd-nginx ./nginx``

This is a screenshort of the deployments:
![Deployments](deployments.png "Deployments")