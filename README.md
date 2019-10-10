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
    
    
        