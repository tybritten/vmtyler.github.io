---
layout: post
status: publish
published: true
comments: true
title: "Deploying Spring Boot Applications on IBM Bluemix"
categories:
- cloud

---

If you’re not a Java developer (neither am I), you might not know about some of the newer technologies that are starting to get popular. These tools are all about getting java applications built and running faster. The focus is on lightweight application servers that boot quickly and have a simple configuration that only builds runtimes with the essential components. For example, the latest version of IBM WebSphere, called [Liberty](https://developer.ibm.com/wasdev/websphere-liberty/) is designed in this manner with a footprint under 60MB and boot times under 2 seconds.

### Spring Boot

Another very popular example comes from [Spring.io](https://spring.io) called [Spring Boot](http://projects.spring.io/spring-boot/). For people already using the Spring framework, Spring Boot is a great way to quickly get an app up and running. These type of tools are a change from previous java application development and deployment methodologies. Steve Perkins has a good post explaining the advantages of [Spring Boot Here.](http://steveperkins.com/use-spring-boot-next-project/)

### Spring Boot on Bluemix

One of the great things about [Bluemix](https://www.bluemix.net) is developers have tons of options for how they want to build and deploy their applications. If you like docker, and want to deploy your spring boot app to Bluemix with a docker container, a fellow IBMer did a [great post on it here](http://heidloff.net/article/Deploying-Spring-Boot-Applications-to-Bluemix-as-Docker-Containers).


What if you would rather deploy your Spring Boot application on Cloud Foundry? Let's do this!

* First, make sure you have the Cloud Foundry CLI installed and the build manager of your choice (I'm using maven).
* Next, let's get a copy of the Spring Boot repo with the sample apps.


``` git clone https://github.com/spring-projects/spring-boot.git
```

* Now, we need to pick a sample app- let's use the web-ui sample.


``` cd spring-boot/spring-boot-samples/spring-boot-sample-web-ui
```

* We need to build the app so we can have it ready to deploy.


``` mvn package
```

* Once it's done we have a JAR that we can deploy to Cloud Foundry. We'll use the '-p' flag to specify the JAR we just created.


``` cf push tbspring -p target/spring-boot-sample-web-ui-1.3.1.BUILD-SNAPSHOT.jar 
```

In this case we didn't supply a buildpack so Cloud Foundry used the default java buildpack. For Bluemix, this is the Liberty for Java buildpack. What if we don't like that? What if we want to use the community java buildpack? It's just as easy as using the '-b' flag and supplying the url to the buildpack:


```  cf push tbspring -p target/spring-boot-sample-web-ui-1.3.1.BUILD-SNAPSHOT.jar -b https://github.com/cloudfoundry/java-buildpack.git
 ```

 When it's done, we have a running Spring Boot app on Bluemix Cloud Foundry. Pretty easy.
