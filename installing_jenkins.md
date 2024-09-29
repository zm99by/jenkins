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

## Running the Jenkins WAR as a standalone application

Run the Jenkins WAR as a standalone application from the command line. This uses an embedded application server (Jetty) and provides some extra features (restart from the web interface and others).

```bash
$ java ${JAVA_OPTS} -jar jenkins.war ${JENKINS_OPTS}
```

The following command line options are configured by startup flags (JENKINS_OPTS):

- `--prefix $PREFIX` (default: `/`)  
  Runs Jenkins to include the `$PREFIX` at the end of the URL.

- `--httpPort $PORT` (default: `8080`)  
  Jenkins listens on `$PORT` port.

- `--httpListenAddress $HTTP_HOST` (default: `0.0.0.0`)  
  Binds Jenkins to the IP address represented by `$HTTP_HOST`.

- `--logfile $LOGFILE`  
  Write to `$LOGFILE` instead of stdout.

These flags are passed as members of the JENKINS_OPTS variable, mentioned earlier.

- See [Starting and Accessing Jenkins](https://www.jenkins.io/doc/book/installing/#starting-and-accessing-jenkins) for a complete list of start-up flags that are available.
- Caveat: If you misspell an option, Jenkins ignores it rather than generating an error.

The standalone application reacts to `SIGTERM` and `SIGINT` to initiate a proper shutdown. The log file is reopened when it receives a `SIGALARM` to allow log rotation.

The following configuration example makes the Jenkins instance reachable only on [http://127.0.0.1:8081/ci](http://127.0.0.1:8081/ci).



