Jenkins is distributed on many channels, including:

- OS native packages (RPM, DEB, and others)
- WAR file
- Docker image
- Cloud templates (AWS, Azure, and others)

Start from the [Jenkins download page](https://www.jenkins.io/download/).

## Installing from Linux packages

Native packages are available for major Linux distributions. The major ones are:

- RPM for Red Hat family.
- Deb for Debian/Ubuntu.
- Linux Mint, OpenSUSE, and many others.

Pattern with package managers:

- Add the Jenkins Package Repository.
- Install and start Jenkins.

An example for the Red Hat family (note, these commands may need `sudo` appended for proper permissions):

```bash
# Add the Jenkins Yum Package Repository
$ wget -O /etc/yum.repos.d/jenkins.repo "http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo"
$ rpm --import "http://pkg.jenkins.io/redhat-stable/jenkins.io.key"
# Install it
$ yum install jenkins
# Start it
$ service jenkins start
```
Linux Native Packages are based on the **standalone** `jenkins.war` files (with an embedded Jetty Application Server). They install Jenkins and do the following:

- Create a jenkins user.
- Set up service scripts (init.d, upstart or systemd).
- Follow native conventions for configuration files.
- Provide log rotation out of the box.

File locations are:

- Settings are located in `/etc/sysconfig/jenkins`
- `$JENKINS_HOME` defaults to the location `/var/lib/jenkins`

## Installing on Microsoft Windows

Run one of the following:

- `setup.exe`
- `jenkins.msi`, if .NET 2.0 runtime is already available

These scripts install Jenkins as a Windows service with files installed into the `%JENKINS_HOME%` folder.

The Web Application Archive (WAR) distribution of Jenkins can be run as a standalone application or in a servlet container.


