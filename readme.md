# Fat Jar vs Thin Jar

### This is sample hello world project with JodaTime dependency.

https://stackoverflow.com/a/57592130

## 1- Run Thin Jar
Run this command:
Thin jar made executable via maven-jar-plugin. Check pom.xml for more details.
```bash
java -jar test-1.0-SNAPSHOT.jar
```
And get:
```
Exception in thread "main" java.lang.NoClassDefFoundError: org/joda/time/LocalDateTime
        at org.example.Main.main(Main.java:8)
Caused by: java.lang.ClassNotFoundException: org.joda.time.LocalDateTime
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:581)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:178)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
        ... 1 more
```
Because thin jar has no jodatime dependency inside.

### Run Thin Jar And Specifing ClassPath

```bash
java -cp 'test-1.0-SNAPSHOT.jar:libs/*' org.example.Main
```

## 2- Run Fat Jar
Fat jar is compiled via maven-assembly-plugin. Check pom.xml for more details.
```bash
java -jar test-1.0-SNAPSHOT-jar-with-dependencies.jar
```
