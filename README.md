## Welcome to Henry's Google Summer of Code Project Blog

### About:

<img align="right" src="Henry_Smith_CS50.jpg" height= "250" width="200" />

My name is Henry Smith, and I am a rising junior at Yale College majoring in Statistics & Data Science with an interest in U.S. government, specifically political communication between elected officials and their constituencies. For my Google Summer of Code project in collaboration with Red Hen Lab, I will be working with mentors [Jungseock Joo](http://home.jsjoo.com/) at the University of California, Los Angeles and [Sumit Vohra](https://www.linkedin.com/authwall?trk=gf&trkInfo=AQF46VQT8HsnZwAAAXIUesZQlLHEC_YJjPOrZoXZPgUeXgBJYK7eTaLs0b2ATrdG6kaP8ucfy_419uoPg6UMRNVnUkIadUS_qCdwAaUu2YoCv7EldRUVNnJg9KsJtgf73FXTUKc=&originalReferer=http://www.redhenlab.org/summer-of-code/red-hen-lab-gsoc-2020-projects&sessionRedirect=https%3A%2F%2Fin.linkedin.com%2Fin%2Fsumit-vohra-224484a0). The project will focus on understanding how Democratic politicians communicate with racial, sexual, and gender minority voters through social media visual imagery. By the generosity of Dr. Joo and his colleagues, images will be sourced through a dataset compiled from politician Facebook accounts during the 2018 U.S. midterm election cycle. 

The complete proposal can be found in my [Github repository for the project](https://github.com/smithhenryd/GSoC_2020_MinorityMessagesAndDemocrats-/blob/master/Henry_SmithSummerResearchProposal.pdf).

#### Contact Information:
I am always excited to receive feedback on my work or meet new people, so feel free to reach out to me using any of the following platforms.

- Email: henry.smith@yale.edu
- Facebook: [Henry Smith](https://www.facebook.com/profile.php?id=100023679815464)
- Github: [smithhenryd](https://github.com/smithhenryd) 

### Blog:

Throughout the summer, I will document progress on my Google Summer of Code project through weekly blog posts. The posts are ordered with the most recent posts presented first:

#### II. Community Bonding Period 05-18-20:

The Google Summer of Code has officially started, and it is off to a great start! In this blog post, I will summarize progress that I have already made as well as actionables that I see as achievable in the near future.

- **Software setup**: With the help of the other students, I have successfully connected to the Case Western Reserve University HPC and have established a home directory in Gallina, Red Hen Lab's server. However, I am still in the process of creating a Singularity container in which I will run the code for my project, as is required by the collaborative. I have not had any prior experience with Singularity nor am I  a master of the terminal window, but I am trying my best. A more complete guide to connecting to the Case HPC is included in blog entry I.

- **2018 U.S. Midterm Elections Images Dataset**: Unlike a majority of the other Red Hens participating in the GSoC, I will not be using the UCLA television news dataset but rather a novel dataset collected by Dr. Jungseock Joo and his colleagues consisting of Facebook images published by politicians during the 2018 U.S. election cycle. As outlined by my proposal, I will use this data to better understand how Democratic politicians communicate with racial, sexual, and gender minority consistuents. 


<img src="Sample_imgs.jpg" />

_Fig. 1: What does it mean for an political image to appeal to a minority group? Clearly the right image (Darren Soto, FL, U.S. House of Representatives) appeals to Hispanic voters much more so than the left (Bill Nelson, FL, Governor candidate), but how is this quantified?_

  - The first challenge, showcased by the two sample images from the dataset included above, is determining **how to measure an image's appeal to a given minority group**. My goal is to observe and annotate a random sample of 2,000 images from the dataset to gain a better answer to this question. Potential explanations are included as follows:
    - [x] Race & ethnicity of individuals 
     - How do we distinguish between the race & ethnicity of the _politician_ versus potential _other individuals_ included in the images?
    - [x] Symbols (ex. flags)
    - [x] Perhaps there are certain cultural elements that cannot be explained or captured so explicitly
     - How do we account for these subtleties in the set of variables measured for the polticial images?

Ultimately, the goal of this discussion is to determine **how to construct a set of variables for each image in the dataset which measures its appeal to the afermentioned minority groups**.
  
  - Additionally, we would like to measure **covariates** that can later be included in a multivariate linear model. While quantifying the appeal of an image to a given minority group is interesting, determinining whether there are statistically significant differences in the content of images along covariates provides a more detailed analysis regarding _how_ politicians use these images to appeal to these voters. Many of these covariates may be measured using existing computer vision technology. Potential covariates include:
    - [x] Race & ethnicity of politician
    - [x] When image was posted (pre or post-primary election)
    - [x] Topic of image (ex. education, public health)
    - [x] Personality dimensions of image (ex. patriotic, threatening)

As you can see, there is a lot of complexity to consider when building this new collection of minority appeal variables and related covariates for the 2018 political images dataset. I will begin my GSoC project by critically examining each of these questions outlined prior to jumping into constructing a prediction model.

#### I. Connecting to CWRU HPC and Singularity
