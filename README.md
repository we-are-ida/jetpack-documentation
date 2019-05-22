# Jetpack - Documentation
(powered by iDA Mediafoundry)

As discussed in [this article](https://medium.com/ida-mediafoundry/aem-tech-component-documentation-97c833a9cda0), we already explained how we could add documentation to a component by adding a REAMDE.md file and changing the `helpPath` property on a dialog. 

This tool will extend this functionality, allowing you to add a README.md file anywhere in the JCR.
The README.md file can be linked to from component documentation.

The link to be used exists of 2 parts:
- Documentation page (fixed) /apps/jetpack/documentation/content/details.html
- Link to a node in the JCR under which the README.md is located. (variable)

example:
A component will use an existing element which was created for reuse at the following location:

`/apps/project/element/reusable-element`

The component requires to have documentation but you wouldn't want to explain what this element does each time a component uses it.
Therefor you can link to the README of the element with the following link:

`/apps/jetpack/documentation/content/details.html/apps/project/element/reusable-element`

As the README is located in the JCR, it's not necessary to add a host to the link.

## Modules

The main parts of this projects are:

* core: Java bundle containing all core functionality like OSGi services, Sling Models and WCMCommand.
* ui.apps: contains the /apps part containing the html, js, css and .content.xml files.


## How to build

To build all the modules run in the project root directory the following command with Maven 3:

    mvn clean install

If you have a running AEM instance you can build and package the whole project and deploy into AEM with  

    mvn clean install -PautoInstallPackage
    
Or to deploy it to a publish instance, run

    mvn clean install -PautoInstallPackagePublish
    
Or alternatively

    mvn clean install -PautoInstallPackage -Daem.port=4503

Or to deploy only the bundle to the author, run

    mvn clean install -PautoInstallBundle


## Testing

There are three levels of testing contained in the project:

* unit test in core: this show-cases classic unit testing of the code contained in the bundle. To test, execute:

    mvn clean test
