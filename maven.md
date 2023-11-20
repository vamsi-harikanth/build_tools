# Maven: (build tool)
  Apache maven is a software project managment tool based on POM- project object model

sequence of steps are:
```
    srccode from repo---> maven (dependencies--build-unittest --deploy)compile--> testing --> package as artifacts( outcome of source code) --. push to repo.
```
 setup from developer perspective
 ```
 install java-> jdk download--> java SE as maven depends on java
 setup java environmental variables--> to work from anywhere.
      systemvariables--edit--> path--add java path till bin.
                     --add--->JAVA_HOME=<add java path excluding bin>
 ```
 check for java -version
           javac
 install eclipse in developer machine and then no need to install maven 
 
 #maven_cordinates:
 ```
 groupid:org.apache.maven
 groupid acts much like javapacakging structuredoes in operating system.
 EX:org.codehaus.mojo-- here the group lives within the directory $m2_repo\org\codehaus\mojo
 GroupId can be same all over the organisation but artifact id is unique
 ```
 ```
 ArtifactId:usaully name of project depicted as $m2_repo\org\codehaus\mojo\vamsi_project
  ```
```
Version:
$m2_repo\org\codehaus\mojo\vamsi_project\12.0
```
```
Packaging  done by combining groupid:artifactid:version
EX: com.catlin.axaxl.first_demo-project.1.0-snapshot
snapshot is marked for code/artifact which is not tested completely and not production ready.
The first, and most common way, is to set the packaging for your project via the equally named POM element <packaging>. Some of the valid packaging values are jar, war, ear and pom. If no packaging value has been specified, it will default to jar.
```
all these are mentioned in POM.xml which is a dependency file.

# steps in build process:
```
compiling surce code --(converting app.java &app.test.java--to class filesapp.class&app.test.class) --- running test cases --packing as jar/war/ear-- deploying to server.
```
# what are maven goals?

Build life cycle:
```3 built in life cycle--1. default, 2. clean , 3. site
refer:  - Link: https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Lifecycle_Reference
```
# important maven goals
clean
validate
compile
test-compile
test
package
verify
install
deploy

-------------------------
## What is POM.xml.
project object model is a fundamental unit of work in maven . its an xml file that contains information about project and configuration details used by maven to build the project.

# dependencies, Plugins(goals indirectly)

# Transtive dependency: 
 we got more dependencies without explicitly adding in pom.xml  ex: junit needs hamcrest-core
 
 ------------------
 Local repository:whenever we run mvn install , local repo created by default in user home dir with .m2 (contains dependencies)
 # how to set up maven enterprise -repository?
  
  Path:users\vamsi\.m2\repository\com\demo\first_demo_sanpshot.jar
 # for deploy it needs  central repo:
 maven central repo contains various plugins (dependencies)
 https://repo1.maven.org/maven2/
 
 once developer pushes code  , devops engineer needs to build the environment or run it
  m2 --repository --com (where mvn install dowload packages)
unless comiple - we cannot see target folder.
 important folders in maven:
 
 -----
 #settings.xml:
 contains elements used to define values which configure maven executions in various ways like pom.xml, but should not be bundled to any specific project
 includes locla repos, alternate remote repository servers, and authentications information.
 
 to deploy an app in tomact from maven
 1. pom needs to be updated with tomcat plugin  and configuration
 2. servers.xml needs to have server details in  id, username, password.
 3. goal as :mvn tomcat7:deploy
 
  
