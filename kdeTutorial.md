# Kernel Density Estimation

---
### Objectives
We want to be able to understand the questions:
* What is a kernel? Not that of your pre popped corn, or your high ranking military officer, the kind that matters to statistics!
* How can kernels be used to understand a set of data?
* What are a few useful applications of kernel density estimation?
* How can the R package TDA be of use in doing so?
- - - 
# What is a kernel?
To begin, visualize a number line with points lying along it, as follows:
---
![Number Line](kdeNumberLine.png)
---
Now, above each point we can insert a Gaussian curve
---
![Kernels on line](kdeKernelsonLine.png)
------
---
We call the curves inserted above these points kernels. In this example, we've chosen to use Gaussian curves as kernels, 
though other implementations include:
* Rectangular kernels
* Triangular kernels
* Biweight kernels
* Uniform kernels
* Cosine kernels
* Epanechnikov kernels

#### However, for functional purposes we are primarily concerned with Gaussian and Epanechnikov kernels specifically. We've seen some exposure to Gaussian kernels, and Epanechnikov kernels are conceptually quite similar but are parabolic rather than normally distributed in nature.
* Gaussian kernels are specifically useful since they are naturally distributed. This yields a natural sort of probability in location for each data point, and when taken as a sum of all the points in a data set is actually quite effective in representing the data. A Gaussian kernel K(u) is defined to be: 

    ![Gaussian formula](kdeGaussianformula.png)
---
* Epanechnikov kernels are useful in their own right, and are representative of data in a manner similar to Gaussian kernels. However, the difference in Epanechnikov kernels lies in their parabolic structure. The function for an Epanechnikov kernel K(u) is defined as: 

    ![Epanechnikov formula](kdeEpanechnikovformula.png)
---
Summing all of our Gaussian kernels together, we gain a nice visualization of the densities of the original points on the number line
---
![Kernel Sum](kdeKernelSum.png)
---
Conceptually, this is the central goal of kernel density estimation. In order to understand sets of data, it is incredibly useful to project their densities in some manner above a set in order to view similarities in their values and to view data in a more probabilistic manner. Adding dimensions, for an n dimensional set of data, we find an n + 1 dimensional kernel density estimate. Thus, for a set of 2 dimensional data, we can construct a similar density visualization in R<sup>3</sup>.

Consider the position of some occurance of data on a plane. We can visualize the density of that data positionally by different 3 dimensional plots of kernel density, each plot referring to a specific variable which we are concerned with positionally. This graph comes from a paper on geolocation, considering the densities of particular words geographically on Twitter.

![Word Densities](wordDensities.png)


---
## Applications of kde
Kernel density estimation is widely applicable as a relatively intuitive, nonparametric method to model the structure of a data set. Below are just a few of countless applications kde can have
### GIS
* kde is immediately applicable to any sort of map, as it is an easy way to understand the densities of a particular phenomenon in a space. One pertinent example comes with the graph included above, when considering the densities of word use on Twitter in specific regions. This instance brought up in ["Kernel Density Estimation for Text-Based Geolocation"](https://www.aaai.org/ocs/index.php/AAAI/AAAI15/paper/view/10034 "kde in geolocation") is easily extended to countless data distributed geographically.
### Econometrics
* Understanding the probability involved with economic data. Econometricians can utilize kde in order to understand the overall trends in economic data, in hopes to explain the root causes of economic trends. For more information, see 
[kde in econometrics](https://arxiv.org/abs/1212.2812 "kde in econometrics").
### AI
* In artificial intelligence, it is useful to understand the probabilistic nature of the world. 
---
## kde in the R package 'TDA'
[R package](https://www.rdocumentation.org/packages/TDA/versions/1.6.2/topics/kde "kde R Documentation")
---
Kernel density estimation can be accomplished by use of the R package 'TDA' through the kde function. By this means, it is possible to input data and recieve an actual numerical assessment of kernel density on that data. 

The kde function considers:
* Two input matrices, one corresponding to each point in a data set of concern, and the other corresponding to a base grid from which the matrix refers to.
* A smoothing parameter in order to mitigate some level of statistical noise in the data if necessary.
* The type of kernel desired- allowed to be either Gaussian or Epanechnikov
* A weight parameter which allows certain data points to be weighted more or less in the kernel density, prioritizing or deprioritizing aspects of the data if useful



