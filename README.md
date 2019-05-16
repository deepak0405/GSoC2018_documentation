# Content Oriented Printer Autoselection : GSoC 2018

<p align="center">
<img src="https://github.com/deepak0405/GSoC2018_documentation/blob/master/b.jpg" width="600" height="350">
</p>

My name is Deepak Patankar and  I was involved in GSoC'18 with **OpenPrinting** under The Linux Foundation working on **Content Oriented Printer AutoSelection**

  - Mentor : **Till Kamppeter**
  - Project Link : https://summerofcode.withgoogle.com/projects/#6531939176022016
  - Tests Done : https://docs.google.com/spreadsheets/d/1TyF2G7qi_18TxgploEhfFnV2c8qbcaoSAbGLXAI1EJU/edit#gid=0

***
### About the project
To print a document, one first needs to select a printer and then adjust its settings to fit their requirement. This project aims at enhancing user experience by building a module which automatically selects a printer based on printing options given by the user. The user need not worry about what all printers are available and their capabilities. Depending on printing options set by the user such as color scheme, paper size, the system will automatically send the job to the best available printer and will notify the user about the same.
***
### My Tasks

1. [PPD Generation for Remote Cups Queue] - Earlier for remote cups queues, ppd file was received from the server, after these changes the ppd file for remote cups queue is generated using the IPP Response message sent by the server which contains all the printer attributes.   
2. [Clustering Remote Cups Queue and IPP Network Printer] - This commit allows clustering remote cups queue and IPP Network printer together in a queue. For the same following changes were done:
    * Changed implicitclass backend, so that job is directly sent to the printer, rather than queuing job on the local cups server.
    * Changed cups-browsed.c, so that now it sends the uri of the printer to the implicitclass backend.
    * For Load Balancing Type *queue_on_server*, changed cupsGetJob function so that number of jobs is directly queried to the printer.
3. [Generating Merged Attributes for the Cluster]: Generated an ipp_t* which contains combined attributes for all the printers in the cluster.
4. [Generating Conflicts for the printer]: Generated cups Array which contains the constraints in the cluster, i.e. pair of attributes which can't be satisfied by any printer in the cluster.
5. [Generating Cluster PPD File]: This commit facilitates generation of ppd file for the cluster, which contains options supported by all printers in the cluster and the constraints. 
6. [Selecting the default attributes of the printer]: The printer with the maximum throughput will be the default printer of the cluster. The default values such as pagesize, media-size of the printer, will be the default value of the cluster.
7. [Selecting the printer for the job]: Based on the job settings requested such as pagesize, media-size, media-type, we will
 select the best printer in the cluster.
8. [Filtering job on the server]: Earlier the job was sent to the client cups server using implicitclass backend unfiltered, but now the job will be filtered at the server itself to the required pdl. A new filter pdftopippprinter.c was added which converts the pdf job to the best pdl supported by the printer.

***
### Commits Link

All the commits can be accessed at [Commits](https://github.com/deepak0405/cups-filters/commits?author=deepak0405).
***
### Issues Created
- [pwg-raster-document-type-supported Invalid value](https://github.com/istopwg/ippsample/issues/156#issuecomment-411157280)
- [Error while Generating Manual Cluster using "Cluster" option in cups-browsed.conf](https://github.com/OpenPrinting/cups-filters/issues/94)
***

### Acknowledgement
I am thankful to my mentor Till  for his guidance throughout the project. I have learnt a lot during the project and interacting with him was a great learning experience for me. I gained a lot of knowledge about system printing, working in linux and writing good readable code.
***

### Useful Links
- [IANA IPP Repository](https://www.iana.org/assignments/ipp-registrations/ipp-registrations.xml)
- [Cups Implementation of IPP](https://www.cups.org/doc/spec-ipp.html)
- [PPD File Specification](https://www-cdf.fnal.gov/offline/PostScript/5003.PPD_Spec_v4.3.pdf)
- [Job Attributes RFC](https://tools.ietf.org/html/rfc2911#section-4.2)
- [Job Attributes LF](http://ftp.linux-foundation.org/pub/openprinting/jobticket/IPP_Mapping/IPP%20Attributes%20for%20Job%20Creation%20operation.pdf)
- [Job Attributes Complete Explanation](http://ftp.pwg.org/pub/pwg/candidates/cs-ippprodprint10-20010212-5100.3.pdf)
- [IPP Attributes Documents](https://tools.ietf.org/html/rfc8011#section-5.2)
- [List of IPP Attributes](https://www.pwg.org/ipp/ipp-registrations.xml)
- [IPP Tutorial: Michael Sweet](https://ftp.pwg.org/pub/pwg/ipp/wd/wd-ippguide-20180430.html)
- [Reading output of child process using pipe](http://www.microhowto.info/howto/capture_the_output_of_a_child_process_in_c.html)
- [Pipes Explained](https://stackoverflow.com/questions/11635219/dup2-dup-why-would-i-need-to-duplicate-a-file-descriptor)
- [Things to keep in Mind for pipe](https://stackoverflow.com/questions/29154056/redirect-stdout-to-a-file/29154328#29154328)
- [AutoGen Explained](http://inti.sourceforge.net/tutorial/libinti/autotoolsproject.html)
- [Make install configure](https://thoughtbot.com/blog/the-magic-behind-configure-make-make-install)
- [Linkers](https://www.lurklurk.org/linkers/linkers.html)
***
   [PPD Generation for Remote Cups Queue]:<https://github.com/deepak0405/cups-filters/commit/8ac1ac32878cd8f91b6fd08069cd629a569a779f>
   [Clustering Remote Cups Queue and IPP Network Printer]: <https://github.com/deepak0405/cups-filters/commit/08ce14be85a07bc74e4eaf85a7e75ecf4a292ebe>
[Generating Merged Attributes for the Cluster]: <https://github.com/deepak0405/cups-filters/commit/ca2870334d0fb78eef00ecba586d87b15f46b3ae>

   [Generating Conflicts for the printer]: <https://github.com/deepak0405/cups-filters/commit/ca2870334d0fb78eef00ecba586d87b15f46b3ae>
   [Generating Cluster PPD File]: <https://github.com/deepak0405/cups-filters/commit/efe3c6f5ac41fdc53817907acbc875dfe4f67453>
   [Calling filters: you can directly use function from schedular to call the filter]: <https://wiki.debian.org/ThecupsfilterUtility>
   [Selecting the printer for the job]: <https://github.com/deepak0405/cups-filters/commit/0dbd11ab6547894499f99f5d41c2ff4f3c149c5c>
   [Filtering job on the server]: <https://github.com/deepak0405/cups-filters/commit/ba2252d0f7acae64aafb05023f57dbb3df6cdad8>
   [Selecting the default attributes of the printer]: <https://github.com/deepak0405/cups-filters/commit/92dc4b687f0de19237fc94cef4c222e82de78915>
   
  
