# spring-batch-rest

[![Build Status](https://travis-ci.org/chrisgleissner/spring-batch-rest.svg?branch=master)](https://travis-ci.org/chrisgleissner/spring-batch-rest)
[![Coverage Status](https://coveralls.io/repos/github/chrisgleissner/spring-batch-rest/badge.svg?branch=master)](https://coveralls.io/github/chrisgleissner/spring-batch-rest?branch=master)

REST API for Spring Batch, based on Spring MVC and Spring Boot.

## Util

[AdHocScheduler](https://github.com/chrisgleissner/spring-batch-rest/blob/master/util/src/main/java/com/github/chrisgleissner/springbatchrest/util/adhoc/AdHocScheduler.java)

Ad-hoc scheduler to register and trigger Spring Batch jobs using Quartz CRON triggers at run-time rather than Spring
wiring time. This allows for simplified set-up of a large number of jobs that only differ slightly.

Example:
```java
adHocScheduler.schedule("jobName", () -> job, "0/30 * * * * ?");

```

[AdHocStarter](https://github.com/chrisgleissner/spring-batch-rest/blob/master/util/src/main/java/com/github/chrisgleissner/springbatchrest/util/adhoc/AdHocStarter.java)

Ad-hoc starter to immediately launch jobs and `Runnable`s asynchronously. This simplifies the syntax normally
involved with defining Spring Batch jobs.

Example:
```java
adHocStarter.start("jobName", () -> System.out.println("Running job"), new JobParameters());

```
