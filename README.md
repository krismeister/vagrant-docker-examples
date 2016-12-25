# Deploy to Linode with Vagrant and Docker

This example uses Docker and Vagrant and can deploy to Linode.com.

There are 3 different ways you can run this example.

 * Locally, with Docker only - easiest for development.
 * Locally, with booting a Vagrant VM which then runs Docker - best for mimicking a real server.
 * On a Linode server, Vagrant deploys the entire site to the cloud.

 This example deploys an nginx docker image and puts the files in the `./public` directory into nginx's default site folder.


## Run Locally with Docker

### Docker Interactive Version

This version is appropriate for faster development. You will need to [install docker](https://www.docker.com/products/docker)
```
# Make sure you have Docker installed
docker --version

# Launch an interactive version
docker-compose up --abort-on-container-exit

# Ctrl-C exits

```

### Docker Build Version

```
# Build the image:
docker build -t myImageName .

# Run the image:
docker run --name myInstanceName -P -d myImageName

# Dtop the instance
docker stop myInstanceName

# Destroy the instance
docker rm myInstanceName

# Destroy the image
docker rmi myImageName

```

### Access Local Docker Site
The docker site can be accessed on [localhost/](http://localhost/) (default port 80)

## Run Locally through Vagrant

You will need to [install Vagrant](https://www.vagrantup.com/downloads.html) and a install virtualalization machine, like [Virtualbox](https://www.virtualbox.org/) You *do not* need to install Docker to run the commands below.

```
# Make sure you have the Vagrant Docker Compose plugin
vagrant plugin install vagrant-docker-compose

# Copy the Vagrantfile.EXAMPLE
cp Vagrantfile.EXAMPLE Vagrantfile

# Bootup the machine
vagrant up

# Destroy the machine
vagrant destroy

# Or destroy by ID:
vagrant global-status
# Find ID of instance then:
vagrant destroy <ID>

```

### Access Local Vagrant:

Local Vagrant deploys the `./public` folder on [localhost:8080/](http://localhost:8080/) (port 8080).

#### Edit files live locally.
Edit and add new files in `./public` to see them live on the server.

**Note to VirtualBox Vagrant users:** virtual box has an issue with reloading files live. It involves `sendfile  off;`.

## Deploy to Linode
Make sure the *Run Locally* above works. Read documentation for [Vagrant-Linode](https://github.com/displague/vagrant-linode).

```
# Make sure you have the Vagrant Docker Linode plugin
vagrant plugin install vagrant-linode

# Add your Linode Token to the Vagrantfile
provider.token = "xxxxxxx"

# Bootup the linode machine.
vagrant up --provider=linode

# Push changed ./public files up to linode
vagrant provision

# Stop the linode server
vagrant halt

# Reboot the linode server
vagrant reload

# Destroy the machine
vagrant destroy

```

### Access Site on Linode:
The terminal during `vagrant up` will list an IP address.  Open this IP address in your browser.
