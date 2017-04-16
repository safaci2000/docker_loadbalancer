Build the SSL image. ssl_nginx.  

Bring all all the images except ssl_nginx which is not necessery. 

Scale app up and down as needed via.  

```sh
docker-compose scale app=4 auth=20
```

traffic will be redirected to the various servers within 5 seconds of the changed picked up via DNS. 

# Credits:

Inspired by: https://statusq.org/archives/2016/07/03/7691/

