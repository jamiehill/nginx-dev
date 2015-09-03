Nginx Test
==========

1. Building the image
---------------------

To build this image, simply issue the following Docker command, assuming we want to name the image `nginx-test`.

    docker build -t nginx-test .
    
Docker will step through each of the build instructions in the `Dockerfile` and create our image for us.

2. Running the image
--------------------
    
In order that we constantly see the latest changes to our application files, we need to make the default Nginx web folder, to the local file system location, of the application we've developing.

To specify a local volume, we need to add the path using the -v flag.

The syntax for running the container, is as follows:

    docker run -v <local-directory>:/usr/share/nginx/html:ro -P -d <image-name>

The command
-----------

**-v** Tells Docker to replace the default Nginx web directory, with the directory you specify.

**local-directory** The directory we want to map Nginx to locally.  (see above)

**ro** Dictates that the volume we're exposing will only have `READ ONLY` access.  Can be changed to `rw`, for , you guessed it, `READ WRITE` access

**-P** Tells Docker to map any required network ports inside our container to our host. This lets us view our web application

**-d** Tells Docker to run the container in the background

**image-name** Finally the name of the built image we wish to run.

Finally run
-----------


Putting this altogether, we get:


     docker run -v /Users/jamie/Sites/git/jamiehill/node-nginx-test/app:/usr/share/nginx/html:ro -P -d nginx-test
    
    
    

    
Okay?