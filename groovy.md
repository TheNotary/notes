# Groovy

Groovy is a language built on-top of the JVM that enables a looser type system, optional semicolons, and lot's of leway around closures so the langauge can get away with some of the efficiencies found in languages like closure, javascript and python.


## Build Management

Gradle is used to bundle dependencies and stuff.


## Syllabus

- Hello World
- A CLI app
  - Packages:  http://docs.groovy-lang.org/latest/html/documentation/#_program_structure
- An app that supports using 3rd party dependencies
  - http://docs.groovy-lang.org/latest/html/documentation/grape.html
- An app that includes tests
- A REPL experience, at least with tests:  (blah.inspect(), .dump(), and .toString(), etc...)
- Packaging your library as a maven package/ jar thingy




## Debugging Apps with Gradle

Consider removing any CI/ CD helper lines that might mask out stack traces and such:

gradle.build
```
test {
  dependsOn 'cleanTest'
  testLogging {
    events "PASSED", "FAILED", "SKIPPED", "STANDARD_OUT", "STANDARD_ERROR"
  }
}
```

Also, you can run a single test class:

```
./gradlew test --tests com.example.jenkins.MyTestClassSpec
```

Also, you can run a single test!!!:

```
./gradlew test --tests com.example.jenkins.MyTestClassSpec.'it can do something useful'
```


## Debugging/ Investigating generally...

You can get useful information about an object with these methods...
```
def obj = new SomeObject()
println "Object's methods:  ${obj.metaClass.methods*.name.sort().unique() }"
println "Object's properties:  ${obj.getProperties().toString() }"
```
