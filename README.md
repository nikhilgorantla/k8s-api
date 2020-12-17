# How to View Kubernetes API with Swagger or ReDoc

### Start a reverse proxy to kubernetes api server 

``` 
kubectl proxy --port=8080
```

### Let get the Kubernetes api's 

```
curl localhost:8080/openapi/v2 > k8s-swagger.json
```

### Swagger UI 

```
docker run --rm -p 80:8080 \
      -e SWAGGER_JSON=/k8s-swagger.json \
      -v (pwd)/k8s-swagger.json:/k8s-swagger.json \
      swaggerapi/swagger-ui
```
```
http://localhost/
```

### ReDoc 

```
docker run -it --rm -p 8080:80 \
          -v (pwd)/k8s-swagger.json:/usr/share/nginx/html/k8s-swagger.json \
          -e SPEC_URL=/k8s-swagger.json redocly/redoc
```
```
http://localhost:8080/
```