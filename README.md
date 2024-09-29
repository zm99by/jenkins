# Requirements and planning

Jenkins runs in a Java Virtual Machine (JVM) running on current versions of Linux, Windows, macOS, and UNIX/BSD.

Jenkins can run on either JDK or JRE. For production environments, it is recommended that you run Jenkins on JDK rather than JRE because the extra tools in the JDK are extremely useful when troubleshooting system problems.

Java 8 or Java 11 is required. Jenkins Long Term Support (LTS) runs on Java 11 beginning in Release 2.164.1; Java 9 and 10 are not supported.

> **Note**  
> As a rule, Jenkins only supports LTS JVM releases, so Java 8 and Java 11 are supported. (Jenkins supports JDK 11 beginning in Release 2.164.1.) Java 9 and 10 will never be supported.
