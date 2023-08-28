3. Gradle 

Step 1. Download Gradle 
- https://gradle.org/next-steps/?version=8.3&format=bin

- wget 


Step 2. Unpack the distribution
Linux & MacOS users

Unzip the distribution zip file in the directory of your choosing, e.g.:

$ mkdir /opt/gradle
$ unzip -d /opt/gradle gradle-8.3-bin.zip
$ ls /opt/gradle/gradle-8.3
LICENSE  NOTICE  bin  getting-started.html  init.d  lib  media

Step 3. Configure your system environment

export PATH=$PATH:/opt/gradle/gradle-8.3/bin


Step 4. Verify your installation

gradle -v


Step 5. Create a project dir:

# mkdir gradle-lib-nexus; cd gradle-lib-nexus; 

gradle init 

Select type of project to generate:
  1: basic
  2: application
  3: library
  4: Gradle plugin
Enter selection (default: basic) [1..4] 3

Select implementation language:
  1: C++
  2: Groovy
  3: Java
  4: Kotlin
  5: Scala
  6: Swift
Enter selection (default: Java) [1..6] 3

Select build script DSL:
  1: Kotlin
  2: Groovy
Enter selection (default: Kotlin) [1..2] 2

Select test framework:
  1: JUnit 4
  2: TestNG
  3: Spock
  4: JUnit Jupiter
Enter selection (default: JUnit Jupiter) [1..4] 1

Project name (default: gradle-lib-nexus): 
Source package (default: gradle.lib.nexus): 
Enter target version of Java (min. 7) (default: 8): 
Generate build using new APIs and behavior (some features may change in the next minor release)? (default: no) [yes, no] 

> Task :init
To learn more about Gradle by exploring our Samples at https://docs.gradle.org/8.3/samples/sample_building_java_libraries.html

BUILD SUCCESSFUL in 28s
2 actionable tasks: 2 executed
root@ldap:~/gradle-lib-nexus# 







Step 6. Create a gradle wrapper

In order to ease the life of the programming team, we embed a Gradle wrapper in each Gradle project.

gradle wrapper --gradle-version 5.3.1 --distribution-type all


Step 7: Now we can test the generated Gradle Wrapper
./gradlew --version


Step 9: Create the gradle library

We will use gradle init in order to generate a basic gradle library

./gradlew init --type java-library --project-name marketing

# ./gradlew init --type java-library --project-name marketing

Select build script DSL:
  1: groovy
  2: kotlin
Enter selection (default: groovy) [1..2] 1

Select test framework:
  1: junit
  2: testng
  3: spock
Enter selection (default: junit) [1..3] 1

Source package (default: marketing): 


BUILD SUCCESSFUL in 10s
2 actionable tasks: 2 executed
#

# ls  build/libs/marketing.jar

Step 10: Build the project
# ./gradlew clean build


Step 11: Publish the library to Nexus repository

Create the gradle.properties file
---------------------------------------
repoUser=[your nexus user]
repoPassword=[your nexus password]
---------------------------------------

root@ldap:~/gradle-lib-nexus# cat settings.gradle  |grep -i marketing 
rootProject.name = 'marketing'
root@ldap:~/gradle-lib-nexus# 


Step 12: Update / Append the build.gradle file

With the below paratmeters 
------------------------------------------------------------------
version = '0.0.1'
group = 'ro.trc.common'
sourceCompatibility = '1.8'

apply plugin: 'maven-publish'
publishing {
    publications {
        maven(MavenPublication) {
            artifact("build/libs/marketing-$version"+".jar") {
                extension 'jar'
            }
        }
    }
    repositories {
        maven {
            name 'nexus'
            url "http://192.168.68.130:8081/repository/maven-releases/"
            credentials {
                username project.repoUser
                password project.repoPassword
            }}
    }
}
------------------------------------------------------------------


# ./gradlew clean build publish

