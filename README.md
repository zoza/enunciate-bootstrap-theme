# Enunciate Bootstrap Theme

A theme for REST based services using enunciate rest API documentation generation.

![Overview](//screenshot.png)

## Background

The default enunciate themes leave much to be desired in terms of overall hotness. Use
these themes to spice up your documentations life and produce clean and effective
API documentations for your REST clients.

## How to Use

The instructions below assume maven is your build of choice. So the files and locations
where the theme is extracted are based on this convention.

### Modify your `enunciate.xml`

You need to tell enunciate about your new shiney theme, so go ahead and bring up
your favorite text editor and chop this goodness in...

    <enunciate xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:noNamespaceSchemaLocation="http://enunciate.codehaus.org/schemas/enunciate-1.21.xsd">

      <!-- .... your standard enunciate goes here .... -->

      <modules>
            
        <docs .... css="bootstrap-enunciate.css" freemarkerXMLProcessingTemplate="bootstrap-enunciate.fmt">..</docs>
         
      </modules>
    </enunciate>

### Add Theme to Your Maven Project

Drap and drop the two `bootstrap-enunciate.css` and `bootstrap-enunciate.fmt` into your project. I prefer to put
them in `src/site` of my services project (WAR) but you dont have to... follow your heart.

### Build your project with enunicate

`mvn clean package`

Below is an example from my maven project.

      <plugin>
        <groupId>org.codehaus.enunciate</groupId>
        <artifactId>maven-enunciate-plugin</artifactId>
        <version>${enunciate.version}</version>
        <configuration>
          <configFile>enunciate.xml</configFile>
          <exports />
          <docsDir>${project.build.directory}/site/api</docsDir>
        </configuration>
        <executions>
          <execution>
            <goals>
              <goal>docs</goal>
            </goals>
          </execution>
        </executions>
        <dependencies>
          <!-- any shared model projects your want docs for -->
          <!-- any additional libs for generating clients, for example ruby! -->
          <dependency>
              <groupId>org.codehaus.enunciate</groupId>
              <artifactId>enunciate-ruby</artifactId>
              <version>${enunciate.version}</version>
          </dependency>
        </dependencies>
      </plugin>