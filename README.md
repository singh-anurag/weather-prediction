# weather-prediction

## Requirement Statement:

The application is designed to predict the weather of various cities around Australia. 
Primarily the weather is observed over a period of time and later , using time series analysis, weather conditions are 
like temperature, humidity etc. are predicted. Time-series analysis is the core part of the project. This analysis is achieved using Auto-regressive integrated moving average (ARIMA), a statistical technique, to forecast weather parameters.

Data required for the prediction is sourced from BOM (Bureau of Meteorology, Australia).

Scope of the application can be altered/widened by changing the source of input data.

# Development

## Design and Build
The application is designed using following 
1. Scala
2. SBT (Scala Build Tool)
3. Java


## Getting started with tools

Process of setting up development environment on our PC/Mac so that we can develop the modules assigned. 
Following tasks are prerequisites.

Install java 1.8 version on your PC.
Follow below link for downloading java sdk 
https://java.com/en/download/win10.jsp
Set Environment Variable for Java
JAVA_HOME = C:\Program Files\Java\jdk1.8.0_20

Setup Scala
Download scala v2.10.4 from below mentioned URL
http://scala-lang.org/download/2.10.4.html
Set Environment Variable for scala
SCALA_PATH = C:\Program Files (x86)\scala
    
Setup sbt

Download sbt from below mentioned URL
http://www.scala-sbt.org/download.html
It is an MSI package hence an installation wizard will help you through installation.

Setup Spark

Download spark version 1.6.1 from below mentioned URL
https://spark.apache.org/downloads.html
Its a zipped file. Unzip it an copy/paste it in home directory for convinience.

 
Validate all the components (Explanation by example)

As part of this topic we will see
1. Installation of Scala IDE for Eclipse
2. Develop simple application using Scala IDE
3. Add eclipse plugin for sbt (sbteclipse)
4. Validate the integration of eclipse, scala and sbt

Setup Scala IDE for Eclipse

Before setting up Scala IDE let us understand the advantages of having IDE

1. The Scala IDE for Eclipse project lets you edit Scala code in Eclipse.
2. Syntax highlighting
3. Code completion
4. Debugging, and many other features
5. It makes Scala development in Eclipse a pleasure.

Steps to install Scala IDE for Eclipse

1. Launch Eclipse
2. Go to “Help” in top menu -> “Eclipse Marketplace”
3. Search for Scala IDE
4. Click on Install
5. Once installed restart Eclipse
6. Go to File -> New -> and see whether “Scala Application” is available or not.

Validate Scala IDE for Eclipse

Create a workspace for demo purpose Example => C:\users\anurag\workspace\demo
1. launch Eclipse IDE
2. Select above created workspace for demo purpose
3. Go to left tab Package Explorer and right click.
4. Select Scala Project and give a name to it.
5. A directory structure will be created with source directory named src and 2 library packages
6. delete src folder and right click on project name and create another source folder. Name it as src/main/scala
7. right click on this newely created source folder and create a Scala Object. Name it as "hw"
8. paste below program in this object

It should look like this

object hw {
  def main(args: Array[String]) {
    println("Hello World!")
}
}

save it by pressing ctrl+S. Right click in the workspace and look for option "Run As". 
1. Then select "1 Scala Application"
2. The output will be displayed in console below as  "Hello World!"

## Now we will see how SBT can be integrated with Scala IDE for Eclipse

Steps to integrate sbt with Scala IDE for Eclipse

1. Check whether ~/.sbt/<version>/plugins/plugins.sbt exists, if not
2. Create plugins directory under ~/.sbt/<version> mkdir -p ~/.sbt/0.13/plugins
3. cd ~/.sbt/0.13/plugins
4. Add addSbtPlugin("com.typesafe.sbteclipse" % "sbteclipse-plugin" % "4.0.0") to plugins.sbt
5. Project uses SBT for building and converting the code into a jar

Through command line traverse to workspace location of the project
C:\Users\Utkarsh\workspace\Demo\simple-scala in this case.

Create a build.sbt file with below mentioned parameters:
name := "simple-scala"
version := "1.0"
scalaVersion := "2.10.4"

Now run following command "sbt package". Once completed a target directory will be created with jar file. Naming convention will be as follows 
1. name of project
2. scala version and 
3. application version as mentioned in build.sbt file.
Hence our jar name will be simple-scala_2.10-1.0.jar. Now type command "sbt run" and we will get the output of the program. 
In our case it will be "Hello World!"

However in bigger projects we have to specify main method name in the command to execute it.
The command for the same will be slightly modified as sbt "run-main hw".
Also in case any parameters needs to be passed can be given inside the double quotes.
For example sbt "run-main hw Hello"

## Creation of Jar and Execution
In our case where there are large number of library dependencies, creating a jar utilises assembly.sbt file. Create one assembly.sbt file in project directory inside root folder. Once plugins.sbt and assembly.sbt file is created place it in desired location and traverse to home directory of your project through command line.Type "sbt eclipse" to generate the files Eclipse needs. You may see a lot of output the first time you run the command as SBT checks everything it needs, but at the end of the output you should see a “success” message, like this:

$ sbt eclipse
[info] Successfully created Eclipse project files for project(s):
[info] YourProjectNameHere

## Dependencies

There are certain dependencies in the code with the help of which expected output is achieved.
All dependencies are listed below in an orderly manner 

1. sparkts (For ARIMA timeseries analysis.)
2. spark-code & spark-mllib (For prediction and forecast)
3. joda-time (Date - time utility)
4. json4s (Extracting Geo-cordinates from Google Rest API response json)

Same dependencies are mentioned in build.sbt file. This enables sbt to have all packages installed so as to avoid any conflicts during future course of development.


