# DBPedia Information Extraction Framework

## Project

This fork is created for a project on course [Information Retrieval on FIIT STU](http://vi.ikt.ui.sav.sk), academic year 2014/2015.  
ASSIGNMENT: extract specific data from the dumps of Eglish, German and Spanish Wikipedia.  
Data to extract: templates, disambiguation pages, categories, infoboxes  
  
## Setting up the extractor  
  
Before you start, you need to install tools: Java, Maven 3, Git  
  
First download the source code of the extractor from this repository by command: git clone git://github.com/KDPV/extraction-framework.git  
  
Next move the the extraction-framework directory and build and install the extractor by command: mvn clean install  
  
If the installation fails, you may need to delete the row <module>live</module>, from the pom.xml file.


## License

The source code is under the terms of the [GNU General Public License, version 2](http://www.gnu.org/licenses/gpl-2.0.html).

