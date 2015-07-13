# Enunciate Bootstrap Theme

A theme for REST based services using enunciate rest API documentation generation.

## Theme Preview

![Screenshot](https://raw.githubusercontent.com/terrancesnyder/enunciate-bootstrap-theme/master/screenshot.png)

## Streamlined Navigation

The theme includes navigation to core packages in your project, grouping common POJO/REST objects
together for easy navigation and isolation.

![Navigation](https://raw.githubusercontent.com/terrancesnyder/enunciate-bootstrap-theme/master/nav.png)

## Type & Element Search

Browse and search all types and elements in your project, including searching descriptions using client
side autocomplete. Quickly and easily navigate and explore your APIs.

![Navigation](https://raw.githubusercontent.com/terrancesnyder/enunciate-bootstrap-theme/master/search.png)

## Operations

See the operations and request/responses along with query parameters from your javadocs in a single glance.

![Navigation](https://raw.githubusercontent.com/terrancesnyder/enunciate-bootstrap-theme/master/operations.png)

## Object/Type Detail

Get in-depth information about your types and elements, not only the types information but polymorphic
inheretence and type hierarchy information is included. In addition, easily see where this type is used
by other types and by method/services to get a 360 degree view of how this type is used and where it is used.

![Navigation](https://raw.githubusercontent.com/terrancesnyder/enunciate-bootstrap-theme/master/type.png)

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