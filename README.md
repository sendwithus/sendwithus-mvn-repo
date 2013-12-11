sendwithus-mvn-repo
===================

Update instructions:
--------------------

1. Clone sendwithus/sendwithus-mvn-repo and sendwithus/sendwithus_java to your local machine.
2. Make your changes in the sendwithus_java repo.
3. To build at any time, run `mvn clean install` from the root sendwithus_java directory.  This will also run unit tests.
4. When you're done, increment the <version> in the pom.xml in the root directory and in the client directory (removing '-SNAPSHOT').
5. When any undeployed changes to the sendwithus_java client are made, '-SNAPSHOT' should be appended to the version number to indicate it is in a development state.
6. From the root of your sendwithus_java project, run `mvn -DaltDeploymentRepository=snapshot-repo::default::file:path/to/sendwithus-mvn-repo/releases clean deploy`.  This will build the project and update your local copy of sendwithus-mvn-repo.
7. Push all of the changes in the sendwithus-mvn-repo project to github.
