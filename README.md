sendwithus-mvn-repo
===================

Update instructions:
--------------------

1. Clone sendwithus/sendwithus-mvn-repo and sendwithus/sendwithus_java to your local machine.
2. Make your changes in the sendwithus_java repo, and merge into master.
3. Increment the version numbers in README.md as well as *both* `pom.xml` files (http://semver.org/).
4. Build the project and update your local copy of sendwithus-mvn-repo.  From the root of your sendwithus_java project, run:

    `mvn -DaltDeploymentRepository=snapshot-repo::default::file:PATH/TO/sendwithus-mvn-repo/releases clean deploy`
    
    Be sure to update the `file:PATH/TO/sendwithus-mvn...` part of the command!

5. Push all of the changes in the sendwithus-mvn-repo project to github.


Notes:
--------------------

- To build at any time, run `mvn clean install` from the root sendwithus_java directory.  This will also run unit tests.

- When any undeployed changes to the sendwithus_java client are made, '-SNAPSHOT' should be appended to the version number to indicate it is in a development state.  Remove '-SNAPSHOT' when work has completed.
