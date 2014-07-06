Flask-Docker-Vagrant-Example
============================

Command 'vagrant up' will build the vm and do the following things:

1) Install docker. This is done by vagrant when docker is referenced as a
provisioner. The line in the Vagrantfile is

    config.vm.provision "docker"

2) Build docker image using the Dockerfile tagging the image with the name
skablam/flask. The line in the Vagrantfile is

    d.build_image "/vagrant", args: "-t=skablam/flask".

3) Run the a container using image skablam/flask, forwarding port 5000 in the
container to port 5000 in the vm, and sharing the folder /vagrant in the vm with
/code in the container.

The hello world Flask app can be amended on the host and it the changes
will automatically get picked up within the container because the code is in the
shared folder.
