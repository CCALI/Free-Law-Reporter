The project houses code used to generate the Free Law Reporter. Please note that while the code works on our servers, it will require some modification to work on yours.

17 October 2012

*Restructuring the project so that you can actaully get all of the code to run your very own FLR*

---

Notes on getting things going.

parseXML.php - parses the raw RECOP XML slip opinion files into valid XHTML verified by HTML Tidy. XHTML is required for the .pub files. Once the files are created it uses the PHP CURL library to pass the file to Apache Solr. It requires inlcudes/lib.uuid.php for generation of UUIDs for each document. This file requires PHP CURL and Tidy extensions. This file is intended to be run from the command line and takes 2 arguments: the absolute path to the local RECOP slip opinion directory and the volume number.

flrepubgen.php - Once you have the RECOP files converted to XHTML, use this command line script to descend into the volume directory and create .epub files for each jurisdiction. It takes 2 command line arguments: the volume number, used to locate the directory to descend, and the date of the RECOP feed. It requires includes/EPub.php to assemble and create the .epub file. It can use wkhtmltoimage to render a custom cover image for the volume if you supply a blank cover image otherwise a simple HTML cover is generated. The .epub file generated by this script may not validate properly, but it will display properly in most .epub capable readers.

pro-code - this directory contains code that was written to process over 700K opinions made available by public.resource.org in early 2008. It has been modified to add FLR details and improve the metadata that is included in the HTML files.