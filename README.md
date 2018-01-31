# test-web

## Intellij Gradle Java Web Spring Project with Modules
New --> Project (Java-gradle) --> Group-Artifact-Version --> Next (Use auto import - create directory empty -use customize gradle wrapper) --> Finish

Select project --> New --> Module (Java-gradle) --> (click Add as and given cancel) --> ArtifactId (given module name) --> Next (Use auto import - create directory empty -use customize gradle wrapper) --> Finish


## Project build.gradle (common gradle)
apply from: 'dependencies.gradle'
apply plugin: 'java'
apply plugin: 'idea'
apply plugin: 'application'

# Run Jetty
apply plugin: 'jetty'

repositories {
    mavenCentral()
}

dependencies {
    compile 'org.springframework:spring-core:3.2.0.RELEASE'
    compile 'org.springframework.security:spring-security-core:3.1.4.RELEASE'
    compile 'org.springframework.data:spring-data-mongodb:1.1.1.RELEASE'
    compile 'com.sun.jersey:jersey-bundle:1.18.1'
    compile 'org.codehaus.jettison:jettison:1.3.6'
    compile 'commons-codec:commons-codec:1.9'
}

# Run Jetty
// Embeded Jetty for testing
jettyRun{
    contextPath = "test"
    httpPort = 8080
}


## Module build.gradle (if need)
dependencies {
    compile libraries.spring_core
    compile libraries.spring_security
    compile libraries.spring_data
}
 ##dependencies.gradle
 def spring_version = '3.2.0.RELEASE'
 project.ext.libraries = [
        spring_core: "org.springframework:spring-core:$spring_version",
        spring_security:'org.springframework.security:spring-security-core:3.1.4.RELEASE',
        spring_data: 'org.springframework.data:spring-data-mongodb:1.1.1.RELEASE',
]


## Run Jetty
apply plugin: 'jetty'

// Embeded Jetty for testing
jettyRun{
    contextPath = "test"
    httpPort = 8080
}

