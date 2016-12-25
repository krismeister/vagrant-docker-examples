#Docker Basic nginx example

This is a docker example. You can edit the files in ``./public/`` and see the edits in your browser.

## Building and run the Docker Image

```
#build the image:
docker build -t nginx_basic_image .

#run the image:
docker run --name nginx_basic_instance -p 8080:80 -d nginx_basic_image

#stop the instance
docker stop nginx_basic_instance

#destroy the instance
docker rm nginx_basic_instance

#destroy the image
docker rmi nginx_basic_image
```

## Then visit localhost (runs on port 8080)

 * [localhost:8080/](http://:8080localhost/)
 * [localhost:8080/test.html](http://localhost:8080/test.html)