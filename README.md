# About this Repository

## How it's Used
This repository is part of the Apache Lucene.Net Project.  More specifically, this repository houses the publishable web pages that are propagated to https://lucenenet.apache.org/  which is the **public facing website** for the Apache Lucene.NET project.

The content of this repository is the output of a DocFx build process.  Actually it's the result of two separate DocFx build processes, one for the website content excluding the docs folder, and one specifically for the docs folder.  The DocFx source files for these two areas are located at:

1.	https://github.com/apache/lucenenet/tree/master/websites/site 
2.	https://github.com/apache/lucenenet/tree/master/websites/apidocs

To publish the site, a github action has been created which compiles the site 
from the directories above using DocFx which then produce static file output 
placed in the following directories which are ignored by Git:

1.	https://github.com/apache/lucenenet/tree/master/websites/site/_site/ 
2.	https://github.com/apache/lucenenet/tree/master/websites/apidocs/_site/ 

### asf-site Branch
This output of the git action is then submitted as a pull request to the asf-site branch of this lucenenet-site repo. The files in the asf-site branch are then auto synced by Apache infra to their server which then serves them at this url:  https://lucenenet.apache.org/  The auto syncing typically happens within momemts but could take longer if a large number of files are changed.

Additional information about Apache process can be found at https://infra.apache.org/project-site.html#sitemanagement  however the information here is vague unfortunately but that's how it works in the case of this project.  The static https://lucenenet.apache.org/  website is always hosted based on the files in the asf-site branch which to be clear is located at https://github.com/apache/lucenenet-site/tree/asf-site. 

### master Branch
Currently the master branch of this lucenenet-site repo isn't actually used but we keep it in sync with asf-site in case we want to use it in the future if we ever implement a staging website.

<br>

## Making Website Changes

Making changes to the public facing https://lucenenet.apache.org/ website entails modifying the files located at https://github.com/apache/lucenenet/tree/master/websites/site as mentioned above. These are the DocFx source files.  DocFx works based on templates and overrides and makes heavy use of markdown. By default it has its own internal template including CSS and then there is a [custom template](https://github.com/apache/lucenenet/tree/master/websites/site/lucenetemplate) file and [custom styles](https://github.com/apache/lucenenet/tree/master/websites/site/lucenetemplate/styles) file to override certain aspects of that. 

### Adding Images
Since the static https://lucenenet.apache.org/  website is always hosted based on the files in the [asf-site branch](https://github.com/apache/lucenenet-site/tree/asf-site), it is convenient to place images in the asf-site branch at https://github.com/apache/lucenenet-site/tree/asf-site/images/. Once these images are propagates to https://lucenenet.apache.org they can be included in markdown files by using fully qualified image references like `https://lucenenet.apache.org/images/my-image.jpg`  The advantage of this approach is that when running the DocFx build process on a local dev machine, the static output will be able to render the images handled in this way.

<br>

## Learn More 
Additional website and documentation details, including information about the build scripts, can be found at on the [documentation](https://lucenenet.apache.org/contributing/documentation.html) page.

