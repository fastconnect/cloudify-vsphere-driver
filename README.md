cloudify-vsphere-driver
================
Contains vsphere drivers for cloudify 2.1.1 (http://cloudifysource.org)
Has been tested with openstack essex and vSphere 5.0.

You can download the driver from our Nexus, and package it in a gigaspaces_overrides.zip (you can use maven:assembly to do that, but you should exclude cloudify dependencies for a lighter archive)
The use of gigaspaces_overrides is explained here: http://www.cloudifysource.org/guide/2.1/clouddrivers/tutorial_maven (Packing and Adding to Cloudify)

to build this 

 mvn package

to install: 
 copy target\cloudify-vsphere-driver-1.1-SNAPSHOT.jar 
to:  <cloudify-2.3.1>\lib\platform\esm\cloudify-vsphere-driver-1.1-SNAPSHOT.jar 
And to:  
     <cloudify-2.3.1>\tools\cli\plugins\esc\vsphere\upload\cloudify-overrides\lib\platform\esm\

Here is the POM configuration to include the driver:
```xml
<repositories>
	<repository>
		<id>repo.opensource.fastconnect.org</id>
		<url>http://opensource.fastconnect.org/maven/content/repositories/opensource</url>
	</repository>
</repositories>

<dependencies>
	<dependency>
		<groupId>org.cloudifysource</groupId>
		<artifactId>cloudify-vsphere-driver</artifactId>
		<version>1.1</version>
		<exclusions>
			<exclusion>
				<artifactId>esc</artifactId>
				<groupId>org.cloudifysource</groupId>
			</exclusion>
			<exclusion>
				<artifactId>dsl</artifactId>
				<groupId>org.cloudifysource</groupId>
			</exclusion>
		</exclusions>
	</dependency>
</dependencies>
```

Here is the full URL: https://opensource.fastconnect.org/maven/content/repositories/opensource/org/cloudifysource/cloudify-vsphere-driver/1.0/cloudify-vsphere-driver-1.0.jar


Known Issues
============
The vSphere driver fails to terminate the instances at some point


