# Grails Bug

* Grails version 3.2.7
* Run from Intellij the Gradle bootRun
* Change the ListHomeController.groovy (change the debug text) wait for the recompile and you get the following error on hot deploy

```text
Error 500: Internal Server Error
URI
/
Class
java.lang.IllegalStateException
Message
null
Caused by
The type registry TypeRegistry(id=942820473,loader=sun.misc.Launcher$AppClassLoader) does not know about type id 2156
Trace
    Line | Method
->>  211 | invoke           in org.grails.core.DefaultGrailsControllerClass$ReflectionInvoker
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
|    188 | invoke           in org.grails.core.DefaultGrailsControllerClass
|     90 | handle . . . . . in org.grails.web.mapping.mvc.UrlMappingsInfoHandlerAdapter
|    963 | doDispatch       in org.springframework.web.servlet.DispatcherServlet
|    897 | doService . . .  in     ''
|    970 | processRequest   in org.springframework.web.servlet.FrameworkServlet
|    861 | doGet . . . . .  in     ''
|    846 | service          in     ''
|     55 | doFilterInternal
```

* If you run via grails-app/init/Application.groovy then hotdeploy never works.
* Perhaps similar to https://github.com/spring-projects/spring-loaded/issues/165

