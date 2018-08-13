# Content Oriented Printer Autoselection : GSoC 2018

My name is Deepak Patankar and  I was involved in GSoC'18 with **OpenPrinting** under The Linux Foundation working on **Content Oriented Printer AutoSelection**

  - Mentor : **Till Kamppeter**
  - Project Link : https://summerofcode.withgoogle.com/projects/#6531939176022016

***
### About the project
To print a document, one first needs to select a printer and then adjust its settings to fit their requirement. This project aims at enhancing user experience by building a module which automatically selects a printer based on printing options given by the user. The user need not worry about what all printers are available and their capabilities. Depending on printing options set by the user such as color scheme, paper size, the system will automatically send the job to the best available printer and will notify the user about the same.
***
### My Tasks

1. [PPD Generation for Remote Cups Queue] - Earlier for remote cups queues, ppd file was received from the server, after this changes the ppd file for remote cups queue is generated using the IPP Response message sent by the server which contains all the printer attributes.   
2. [Clustering Remote Cups Queue and IPP Network Printer] - This commits allows clustering remote cups queue and IPP Network printer together in a queue. For the same changes following changes were done:
    * Changed implicitclass backend, such that job is directly sent to the printer, rather than queuing job on the local cups server.
    * Changed cups-browsed.c, such that now it sends the uri of the printer to the implicitclass backend.
    * For Load Balancing Type *queue_on_server*, changed cupsGetJob function such that number of queues is directly queried to the printer.
3. [Generating Merged Attributes for the Cluster]: Generated an ipp_t* which contains combined attributes for all the printers in the cluster.
4. [Generating Conflicts for the printer]: Generated cups Array which contains the constraints in the cluster, i.e. pair of attributes which can't be satisfied by any printer in the cluster.
5. [Generating Cluster PPD File]: This commit facilitates generation of ppd file for the cluster, the ppd file contains options supported by all printers in the cluster and the constraints. 
***
### Commits Link

All the commits can be accessed at [Commits](https://github.com/deepak0405/cups-filters/commits?author=deepak0405).
***
### Issues Created
- [pwg-raster-document-type-supported Invalid value](https://github.com/istopwg/ippsample/issues/156#issuecomment-411157280)
***

### Targets Left
- Selecting printer based on the job attributes given.
- Sending the appropriate filter name to implicitclass backend for the selected printer, and adding functionality in the backend to call the appropriate filter.
- Minor fixes in generating merged attributes, like handling pwg-raster-document-sheet-back.
***
### Acknowledgement
I am thankful to my mentors Till  for his guidance throughout the project. I have learnt a lot during the project and interacting with him was a great learning experience for me. I gained a lot of knowledge about system printing, working in linux and writing good readable code.
***

### Useful Links
- [IANA IPP Repository](https://www.iana.org/assignments/ipp-registrations/ipp-registrations.xml)
- [Cups Implementation of IPP](https://www.cups.org/doc/spec-ipp.html)
- [PPD File Specification](https://www-cdf.fnal.gov/offline/PostScript/5003.PPD_Spec_v4.3.pdf)
***
   [PPD Generation for Remote Cups Queue]:<https://github.com/deepak0405/cups-filters/commit/683d3acb984360b1516e20404497462a7e4f6455>
   [Clustering Remote Cups Queue and IPP Network Printer]: <https://github.com/deepak0405/cups-filters/commit/f7fec6a34dccf82a88e3ecce05eb40f016594829>
[Generating Merged Attributes for the Cluster]: <https://github.com/deepak0405/cups-filters/commit/365990aec31a6f92fe58e0d60113e0932098c526>

   [Generating Conflicts for the printer]: <>
   [Generating Cluster PPD File]: <>
