# classifier-sample

Steps to reproduce bug

If you've built the gradle project successfully already, clear out the gradle cache of netty-transport-native-epoll files

`./mvnw clean install`

`./gradlew clean build`

The maven build should be successful and store the non-classified version of the netty-transport-native-epoll file in the local maven cache.

The gradle build is expected to fail if the bug is present because it will check the mavenLocal cache and find the needed pom file, but the classified jar will be missing.

The desired outcome is that gradle should choose to search additional repositories when mavenLocal is only partially complete.

A workaround is to delete the netty-transport-native-epoll folders in the mavenLocal file structure, but this is undesirable.
