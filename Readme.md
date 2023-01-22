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

