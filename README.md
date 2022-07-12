# Hello Java

This repository demonstrates a problem I stumbled upon when trying to update a project which uses a Xbase DSL from Java 11 to 17.

From Java 14 to Java 15 it's not possible to reference types which are defined in the same project as the DSL anymore.

## Structure
In the [language](language) folder the DSL is located. It's a very simple Xbase DSL which can be used to greet Java types. The grammar is located [here](language/hellojava/src/hellojava/HelloJava.xtext)

Within [sample](sample) you can find a small maven Project which uses the DSL. The project contains a Java type which is referenced in the DSL file. 

## Build
I created a [GitHub Actions matrix build](.github/workflows/maven.yml) in order to demonstrate the behaviour. It installs the language to the local maven repo and tries to build the sample using Java 11 up to Java 17.

As you can see in the [results](https://github.com/OLibutzki/HelloJava/actions/runs/2656339113) it works for Java 11 - 14 and is broken for Java 15 - 17:
```
ERROR:MyType cannot be resolved to a type. (file:/home/runner/work/HelloJava/HelloJava/sample/src/main/java/hellojava.hello line : 1 column : 7)
```
