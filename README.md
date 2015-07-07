# takipi-ebextensions
Install Takipi (https://www.takipi.com) on AWS Elastic Beanstalk 

Requirements
============
Modern Java deployment on Amazon Linux.

Installation
============
Installing Takipi on AWS Elastic Beanstalk requires a eb-extensions file. This file should be named 00takipi.config.

`WebApp`  is a sample maven web project that shows how to pack the config file with your application before deploying it to beanstalk.

Config your eb-extensions file (`/src/main/ebextensions/00takipi.config`) like:
```
packages:
  rpm:
    takipi: https://app.takipi.com/app/download?t=rpm
commands:
  takipi_setup:
    command: "/opt/takipi/etc/takipi-setup-package <YOUR_SECRET_KEY>"
  
option_settings:
  - namespace:  aws:elasticbeanstalk:container:tomcat:jvmoptions
    option_name:  JVM Options
    value:  -agentlib:TakipiAgent
```
Make sure to put your Takipi installation secret key instead  <YOUR_SECRET_KEY>. 

Note to add `-agentlib:TakipiAgent` in the option_settings, in order to monitor your application with Takipi.
 

Use maven or other to pack your your application (war file):

``` mvn package ```

You can view the sample `WebApp/target/WebApp.war`

Usage
=====
Takipi website: http://www.takipi.com

Need help?
=====

Contact us at: [support@takipi.com](mailto:support@takipi.com) or read more at https://docs.takipi.com
