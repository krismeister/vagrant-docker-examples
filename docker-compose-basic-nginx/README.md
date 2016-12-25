#Docker-Compose Basic nginx example

This is a docker composer example. You can edit the files in ``./public/`` and see the edits in your browser.

## Running Example

```
#live interactive version:
docker-compose up
```

## Then visit localhost (runs on port 80)

 * [localhost/](http://localhost/)
 * [localhost/test.html](http://localhost/test.html)

## Building a Docker Image

```
#build the image:
docker build -t myImageName .

#run the image:
docker run --name myInstanceName -P -d myImageName

#stop the instance
docker stop myInstanceName

#destroy the instance
docker rm myInstanceName

#destroy the image
docker rmi myImageName
```
