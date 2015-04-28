# A working example to execute elasticio/apprunner using a custom Framework

# Stuff to do first

- Clone [playa-mesos](https://github.com/iznenad/playa-mesos)
- Spin up the VM with `vagrant up`
- Build the mesos-docker-tutorial jar with `mvn package`
- Copy the created jar to `playa-mesos/framework/framework.jar`
- `vagrant ssh` into playa-mesos VM

Run the framework:

    java -classpath /home/vagrant/framework/framework.jar com.codefutures.tutorial.mesos.docker.ExampleFramework 127.0.1.1:5050 elasticio/apprunner 1 http://elasticio-slugs-stage.s3.amazonaws.com/elastic_nenad/testrepo/slug-849fc4ccd9905f28c59e83dc9ff283bf1744084e.tar.gz

# Notes

To restart the slave: `sudo service mesos-slave restart`
To restart the master: `sudo service mesos-slave restart`
(Both while inside the playa-mesos VM of course)

The execution command will download a dumb slug with an example component containing a setInterval and printing the response from google.com.

The `node main.js` command is hardcoded [here](https://github.com/iznenad/mesos-docker-tutorial/blob/master/src/main/java/com/codefutures/tutorial/mesos/docker/ExampleScheduler.java#L118).

You can see the slave logs [here](http://10.141.141.10:5050/#/slaves). Just click on one of the slaves and find the big LOG link on the left side of the page.
The master logs are on the left side [here](http://10.141.141.10:5050/#/)
