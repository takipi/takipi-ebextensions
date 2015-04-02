# takipi-ebextensions
Install Takipi (https://www.takipi.com) on AWS Elastic Beanstalk 

Requirements
============
Java ( >=1.6 )
AWS Elastic Beanstalk environment

Attributes
==========
Make sure you include your Takipi secret key as custom the /src/main/ebextainsions/00takipi.config file :

```
commands:
  takipi_setup:
    command: "/opt/takipi/etc/takipi-setup-package YOUR_SECRET_KEY"
```

Usage
=====
Takipi website: http://www.takipi.com

To connect Takipi to your Java process add the following JVM argument -agentlib:TakipiAgent before -classpath/-jar.
