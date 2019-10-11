# Maven Crash Course
Maven Crash Course, by Jason Taylor

What is Maven

    build tool
    
    dependency mangement
    
    repository system
    
    plugin framework
    
    best practice

Core concepts

    convention over configuration
    
    Project Object Model (POM)
    
    Dependency resolution
    
    Maven Repository
    
    Lifecycle, Phases, and Goals
    
    Plugin Archtecture
    

Convention over configuration 

    Little / no configuration
    
    Follow prescripted conventions
    
    Best practices
    
    Reasonable defaults
    
    Override when required
    
Project Object Model

    Object-based representation of a build
    
    Project meta data
        
        coordinates (Group, Artifact, Version)
        
    Dependencies 
        
        coordinates (Group, Artifact, Version)
        
    Build settings
        
    Inheritance /Super POM
    
    Build settings 
    
Dependencies 

    Declarative primary dependencies 
    
    Transitive dependencies 
    
    Downloading from repository
    
    Caching locally
    
    Scopes (compile time vs runtime)

    primary-lib.jar <= declared in POM
    
        secondary-lib.jar
            
            3rd-level-lib.jar
            
                etc.jar
                
Maven Repositories 

    Artifact storage
    
    Standard layout
    
    Local or remote
    
    Central (many open source projects)
    
    Private (corporate)
    
    Used by others: Gradle, Ivy
    
 Maven Building Blockes
 
    Goals
        
        Tasks that do the work
        
        define by plugins
        
            mvn compiler:compile
            
    Phases
        
        One or many golas
        
        part of Lifecycle 
        
            mvn compile 
            
    Lifecycle
    
        Start to finish collection of phases
        
        Defferent based on packaging type
        
        Executes all phases up to specific phase 
        
Plugins

    Nearly everything is a plugin
    
    Extends Maven
    
    More Gaoals
    
    Dependencies
    
    
cd maven/bin

    m2.conf		
    
    mvn	
    
        ./mvn -version	
    
    mvn.cmd		
    
    mvnDebug	
    
    mvnDebug.cmd	
    
    mvnyjp
    
Mac Install

    vi ./bash_profile
    
```text
M2_HOME='/Users/girmaenigusse/Development/maven'
export M2_HOME

export PATH="$PATH:$M2_HOME/bin"
```

    echo $M2_HOME
    
    mvn -version
    
Example source code

    github
    
    https://github.com/srctips/maven-quick-start
    
    https://github.com/srctips/maven-course-content
    
Absolute minimum POM

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" 
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
		http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>training.maven.quick</groupId>
    <artifactId>minimal-example</artifactId>
    <version>1.0.0</version>
</project>
```

I could start the build now

    mvn package

groupId is package name in reverse order of your domain name.

artifactId as name of your application or lib

1. Building minimal example 1.0.0
 
```text
[INFO] Scanning for projects...
[INFO] 
[INFO] ----------------< training.maven.quick:minimal-example >----------------
[INFO] Building minimal-example 1.0.0
[INFO] --------------------------------[ jar ]---------------------------------
```
2. Using the resources plugin to gather the resources

```text
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ minimal-example ---
```

3. Using the compile to compile if there is any source code

```text
[INFO] skip non existing resourceDirectory /Users/ffsdfg/IdeaProjects/Maven_Crash_Course/minimal/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ minimal-example ---
```

4. test

```text
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ minimal-example ---
[WARNING] Using platform encoding (UTF-8 actually) to copy filtered resources, i.e. build is platform dependent!
[INFO] skip non existing resourceDirectory /Users/girmaenigusse/IdeaProjects/Maven_Crash_Course/minimal/src/test/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:testCompile (default-testCompile) @ minimal-example ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ minimal-example ---
```

5. maven jarls

```text
[INFO] 
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ minimal-example ---
```

    ls 
    
        pom.xml 
        
        target
            minimal-example-1.0.0.jar
            
 Error
 
 ```text
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.1:compile (default-compile) on project minimal-example: Compilation failure: Compilation failure: 
[ERROR] Source option 5 is no longer supported. Use 7 or later.
```

packaging jar

<version>1.0.SNAPSHOT</version>

    minimal-example-1.0.0.jar
    
    minimal-example-1.0.SNAPSHOT.jar
    
name is a short description of the project.

listing the contents of jar file

    jar -tf target/minimal-example-1.0.SNAPSHOT.jar
    
```text
Girmas-MBP-2:minimal girmaenigusse$ jar -tf target/minimal-example-1.0.SNAPSHOT.jar 
META-INF/
META-INF/MANIFEST.MF
triaining/
triaining/maven/
triaining/maven/quick/
.gitkeep
triaining/maven/quick/HelloWorld.class
META-INF/maven/
META-INF/maven/training.maven.quick/
META-INF/maven/training.maven.quick/minimal-example/
META-INF/maven/training.maven.quick/minimal-example/pom.xml
META-INF/maven/training.maven.quick/minimal-example/pom.properties
```

Build Settings - Changing the Final Name