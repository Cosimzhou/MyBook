Java Building Tools Notes
=========================

* gradle
gradlew info
gradlew tasks
gradlew build
gradlew :<project-dir>:<task>
gradlew :<project-dir>:help


* maven
mvn build
mvn package

* sbt
sbt update
sbt
> compile
> run
> dist
> test
> testOnly ai.deepmap.anga.dao.HeightImageDAOImplTest -- -z ai.deepmap.anga.dao.HeightImageDAOImplTest.testGetAltitude











Writing in Java
================

latLngAlts.stream().
          map(point -> convertLLA2ENU(point)).
          collect(Collectors.toList());

pb enum:
  enum.getNumber()
  Enum.forNumber();

