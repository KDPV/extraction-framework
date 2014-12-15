# DBPedia Information Extraction Framework

## Project

This fork is created for a project on course [Information Retrieval on FIIT STU](http://vi.ikt.ui.sav.sk), academic year 2014/2015.  
ASSIGNMENT: extract specific data from the dumps of Eglish, German and Spanish Wikipedia.  
Data to extract:  
  * templates,  
  * disambiguation pages,  
  * categories,  
  * infoboxes.  
  
## Setting up the extractor  
  
Before you start, you need to install tools: **Java, Maven 3, Git**  
  
First download the source code of the extractor from this repository by command: `git clone git://github.com/KDPV/extraction-framework.git`  
  
Next move the the extraction-framework directory and build and install the extractor by command: `mvn clean install`  
  
If the installation fails, you may need to delete the row `<module>live</module>` from the **pom.xml** file.
  
## Configure the downloader

Before you can start extracting, you need to download some dumps from which you will be able to extract.  
  
You need to create a **.properties** file with the settings for the downloader. You can find the file used in this project in the **dump** directory. The file is called **download.vi_projekt.properties**  
  
At first you need to define the download server and the working directory. All the files will be downloaded there.  
For example:  
`base-url=http://dumps.wikimedia.org/`  
`base-dir=/media/root/vidisk/download`  
  
After that you define which files to download. We will download dumps of the english, german and spanish wikipedia:  
`download=es:pages-articles.xml.bz2`  
`download=de:pages-articles.xml.bz2`  
`download=en:pages-articles.xml.bz2`  
  
You can choose to unzip files after download or not. If not, you can save space, but the extraction will take more time:  
`unzip=true`  

At the end you can configure the connection details. If connecting to the server fails, we try five times with pauses of 10 seconds:  
`retry-max=5`  
`retry-millis=10000`  

When the configuration is completed, you can start the downloading process. If you are still in the **dump** directory, use this command:  
`../run download config=download.vi_projekt.properties`  
  
## Configure the extractor  
  
After you've downloaded the dumps, you can start extracting data. You need to create another **.properties** files with settings for the extractor.  
  
Configuration for this project is placed in the **dump** directory and is called **extraction.vi_projekt.properties**.  
  
The first key-value pair in the file is the working directory. Same as for the downloader. The downloaded dumps must be saved here and the extractor will save the extracted data to this directory, too.  
  
Example: `base-dir=/media/root/vidisk/download`  
  
After that you should define how the source dumps are named. If you've choosed to unzip files after download, add line:  
`source=pages-articles.xml`  
If the value for unzip key in the downloader's config file was false, add this line:  
`source=pages-articles.xml.bz2`  
  
You need to set up languages to extract:
`languages=en,de,es`
In this project we want to extract data from english (en), german (de) and spanish (es) wikipedia.  
  
The most important row in the config file is defining extractors. This is the place, where you tell, which informations to extract from the dumps. We add these extractors:  
`extractors=.DisambiguationExtractor,.InfoboxExtractor,.TemplateParameterExtractor,.ArticleTemplatesExtractor,.CategoryLabelExtractor`  

You should not change other lines in the config file!

If everything is set up, you can start the extracting. From the **dump** directory use command:  
`../run extraction extraction.vi_projekt.properties`  

The extraction will run for several hours (on my pc: 2h for spanish, 4h for german, 16h for english). So leave your computer to work and HAVE A GOOD TIME! :)
  
## License

The source code is under the terms of the [GNU General Public License, version 2](http://www.gnu.org/licenses/gpl-2.0.html).

