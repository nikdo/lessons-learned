# Java

## Maven

Maven builds only modules that has been changed since last build if `clean` command is not passed.

Dependencies are build too, but only for Java packages. Front-end file changes are not detected to run `frontend-maven-plugin`.

To run just a specific test, set `test` property:

```
mvn -Dtest=AppControllerIT test
```

There is a `spring-boot-devtools` plugin that can rebuild modules on file change.

