![html/pdf](https://github.com/metno/data-management-handbook/workflows/html/pdf/badge.svg?branch=master)

# NIVA Data Management Handbook (DMH)

This handbook is based on the [DMP template created by the Meteorological Institute in Norway (METNorway)](https://metno.github.io/data-management-handbook/).

In case of questions regarding the template - please submit an [issue on the original repository.](https://github.com/metno/data-management-handbook)

The current version of this DMP is found on the link below:
 https://nivanorge.github.io/data-management-handbook/ 

## How to use this handbook:

* doc folder: Add only the templates for the chapters and appendices that includes partner specific information (all starting with specialized):
   
	* specialized_intro_template.adoc
	* specialized_data_services_template.adoc
	* specialized_datagov_template.adoc
	* specialized_strudoc_template.adoc
	* specialized_userportals_template.adoc
	* specialized_practical_guidance_template.adoc
	* specialized_appendixB_template.adoc
* To get your organisations visual profile on the DMH, create or add a .yml file with the theme for the handbook.
* The file “data-management-handbook.adoc”, includes the specialized files via variables. These variables are defined in the docker-compose.asciidoctor.yml file. (If one of the partner-specific files does not exist in your local repository, The CI will add the template). This is also the file that sets up the pdf.

## Compiling the documentation
The general part of the documentation can be compiled by running `vagrant up`. You can reuse the code here to add CI and compile your own version. Please ask if you need help.

## Other information
The docker-compose.acdd_elements.yml creates the acdd file via CI. This appendix is relevant for all partners that use NetCDf- files.
