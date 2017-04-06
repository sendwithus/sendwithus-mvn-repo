sendwithus-mvn-repo
===================

Update instructions:
--------------------

1. Clone sendwithus/sendwithus-mvn-repo and sendwithus/sendwithus_java to your local machine.
2. Make your changes in the sendwithus_java repo, and merge into master.
    - Increment the version numbers in `README.md`, `SendWithUs.java`, and *both* `pom.xml` files (http://semver.org/).
3. Build the project and update your local copy of sendwithus-mvn-repo.  From the root of your sendwithus_java project, run:

    `mvn -DaltDeploymentRepository=snapshot-repo::default::file:FIXME/PATH/TO/sendwithus-mvn-repo/releases clean deploy`
    
    Be sure to update the `file:FIXME/PATH/TO/sendwithus-mvn...` part of the command!

4. Push all of the changes in the sendwithus-mvn-repo project to github.

Update with Docker
------------------

If you want to avoid installing all of the Java requirements on your own local machine, perform the steps above within a docker image.

```
docker run -it --rm --name swu-java-maven -v "$PWD":/usr/src/mymaven -v
**PATH to maven repo source**:/usr/src/mvn-repo -w /usr/src/mymaven
maven:3.2-jdk-7 mvn
-DaltDeploymentRepository=snapshot-repo::default::file:/usr/src/mvn-repo/releases
clean deploy
```

Description:
- Run that command from within the `sendwithus_java` directory.
- Important: change the `**PATH to maven repo source**` to the absolute path to the maven directory.
- The first `-v` mounts the local (sendwithus_java) directory to the working directory ('-w') within the docker image.
- The second `-v` mounts the maven repo directory into the docker image also.
- The last part of the command runs maven and sets the output directory to the mounted maven dir where the package is generated.


Notes:
--------------------

- To build at any time, run `mvn clean install` from the root sendwithus_java directory.  This will also run unit tests.

- When any undeployed changes to the sendwithus_java client are made, '-SNAPSHOT' should be appended to the version number to indicate it is in a development state.  Remove '-SNAPSHOT' when work has completed.
