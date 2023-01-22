When deploying application to prod environment, what type of image will be used for the api-deployment?

como se muestra en el prod overlay, es memcached

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: api-deployment
spec:
  template:
    spec:
      containers:
        - name: api
          image: memcached
```
----
How many replicas for api-deployment will get deployed in prod?

2 (ya que no hay nada en los overlays )

-----
What will be the value of the environment variable MONGO_INITDB_ROOT_PASSWORD in the mongo-deployment container in the staging environment?

Si vamos a overlay, vemos que es superpassword123


----
When deploying to prod how many total pods are created?

5

---------------

How many environment variables are set on the nginx container in the api-deployment in dev environment?

Son 3.
1 de base mas dos de aca
```
...
      containers:
        - name: api
          image: nginx
          env:
            - name: DB_CONNECTION
              value: db.kodekloud.com
...



overlays/dev/api-patch.yaml



apiVersion: apps/v1
kind: Deployment
metadata:
  name: api-deployment
.
.
.
      containers:
        - name: api
          image: nginx
          env:
            - name: DB_USERNAME
              valueFrom:
                configMapKeyRef:
                  name: db-creds
                  key: username
            - name: DB_PASSWORD
              valueFrom:
                configMapKeyRef:
                  name: db-creds
                  key: password
```

Update the api image in the api-deployment to use caddy docker image in the QA environment.

Perform this using an inline JSON6902 patch.



Note: Please ensure to apply the updated config for QA environment before validation.


