
Linux Native Packages are based on the standalone `jenkins.war` files (with an embedded Jetty Application Server). They install Jenkins and do the following:

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

These scripts install Jenkins as a Windows service with files installed into the `$JENKINS_HOME` folder.

The Web Application Archive (WAR) distribution of Jenkins can be run as a standalone application or in a servlet container.

## Running the Jenkins WAR as a standalone application

Run the Jenkins WAR as a standalone application from the command line. This uses an embedded application server (Jetty) and provides some extra features (restart from the web interface and others).

