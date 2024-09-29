# Requirements and planning

Jenkins runs in a Java Virtual Machine (JVM) running on current versions of Linux, Windows, macOS, and UNIX/BSD.

Jenkins can run on either JDK or JRE. For production environments, it is recommended that you run Jenkins on JDK rather than JRE because the extra tools in the JDK are extremely useful when troubleshooting system problems.

Java 8 or Java 11 is required. Jenkins Long Term Support (LTS) runs on Java 11 beginning in Release 2.164.1; Java 9 and 10 are not supported.

> **Note**  
> As a rule, Jenkins only supports LTS JVM releases, so Java 8 and Java 11 are supported. (Jenkins supports JDK 11 beginning in Release 2.164.1.) Java 9 and 10 will never be supported.

# Tuning the JVM and operating system

The Java Virtual Machine (JVM) must be tuned using these settings.

- Memory Heap size: -Xms1G -Xmx2G

- G1 garbage collector for heap > 4GB: -XX:+UseG1GC

Check your Java Memory documentation for details.

You might also need to tune your operating system limits, such as:

- Maximum number of open files.

- Maximum number of forked processes.

- Network tuning (packet size, TCP timeouts).

# Disk space requirements

Jenkins writes many files as it processes builds, so it is important to configure high-performance disks with adequate space.

Consider the following when planning disk space:

- Artifacts, logs and other files written by builds can be very large. The retention policy affects the amount of space these consume, so if you need to retain all (or most) artifacts for a long time, the disk consumption issues become very serious.

- Disk usage grows over time, especially if you host jobs from people who are not close to you, so be sure you configure more disks when necessary.

- Backups also require significant amounts of disk storage. You must have enough space on the disk to accommodate the backed up files; therefore, it is recommended that you create a separate file system (mountpoint) for the backup directory.

Best practices for disk space
- Offload artifacts, logs, backups, and other files to external storage such as Nexus or Artifactory so that they are not stored on the Jenkins controller.

- Configure a separate disk on the controller just to hold backups. You can back up Jenkins files to a local director, then copy those files to an external location.

- Big disks are recommended, although it is not necessary to invest in 15000rpm SCSI disks.

- Low latency SSD drives can significantly enhance the performance of the Jenkins cluster.

- Expandable volumes such as LVM on Linux or "spanned volumes" on Windows enable you to create very large virtual disks.

- Disks can be network mounted using either NFS or SAN.

- The Jenkins home directory ($JENKINS_HOME) should be its own filesystem.

# For further reading
[Installing Jenkins](https://www.jenkins.io/doc/book/installing/) discusses various ways to install Jenkins, including on Docker and Kubernetes.

The Initial Settings section gives detailed information about setting network and other parameters and setting up HTTP.

The Tuning Jenkins GC for Responsiveness and stabiliy with Large Instances blog provides background information and useful recommendations.

Scaling Jenkins has more information about hardware requirements and considerations.
