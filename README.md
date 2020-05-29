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

#### III. Preliminary Image Annotation 05-29-20:

Prior to annotating the 2018 Facebook images dataset, we must first determine minority group-specific variables of interest. As cited in the project proposal, a 2017 report by the Pew Research Center estimated that Black voters constituted 19% of the Democratic party, Hispanic voters, 12%, and Asian voters, in combination with other racial and ethnic minority voters, 10% [2]. For the sake of our analysis, in order to obtain a sufficiently large sample of images pertaining to each group, we will measure the appeal of Democratic politicians to **Black, Hispanic, and Asian voters**. Additionally, as our research also seeks to examine political appeal to sexual and gender minority voters, we include a variable **'LGBTQ+\_appeal'**. An exit poll by NBC conducted during the 2018 U.S. midterm election estimated that LGBT voters consititued 6% of the electorate, and 82% of these voters supported the Democratic candidate [1]. Similarly, while LGBTQ+ could be separated into various sexual and gender minority classifications, each subset would likely only pertain to very few images.

As it would be difficult to create a continuous scale on which to measure a politician's intended appeal to a given minority group that is consistent across annotators (what one annotator considers moderate appeal may be different from another), we use a nominal classification. The value = 1 is assigned to images in which the politician had the _intention of_ appealing to the respective minority group, and = 0 is assigned to those in which this intention is not present. 

So to gain a better understanding of the proportion of images to which each minority group-specific variable pertains (i.e.  images such that a given variable = 1), I annotate a random sample of 2,000 images from the Facebook images dataset. Moreover, two seperate analyses are performed: the first in which text-based images are excluded from annotation and the second in which these images are included. 


| Variable            | Total Dem images annotated | 'black_appeal' |  'hispanic_appeal'| 'asian_appeal'| 'LGBTQ+\_appeal' |
| --------------------| ---------------------------| ---------------| ------------------| --------------| -----------------|
| Text imgs excluded  | 843                        | 9.3713%        | 2.8470%           | 2.2539%       | 0.9490%          |
| Text imgs included  | 1027                       | 7.9844%        | 2.8238%           | 2.0448%       | 1.1685%          |


Of course, we are limited in terms of statistical analyses, as the two samples are by no means independent of one another (there are only 184 additional images in the 'text imgs included' set that are not also in the 'text imgs excluded'). However, the data seems to suggests that non-textual more so than textual images are used by Democratic politicians to appeal to minority voters, with the exception of the LGBTQ+ community. The visual appeal to LGBTQ+ voters is primarily symbol-based (rainbow pride flag/banner, Human Rights Campaign logo, etc.) as opposed to the physical presence of LGBTQ+ individuals, which may explain why the difference is present particularly among this group.

As the GSOC coding period comes to an official start, I will next work to formulate questions by which a larger subset of the images will be annotated. Because the proportion of images that intend to appeal to each of the four minority groups is relatively small (as we see from the above results), we may need to build a preliminary prediction model by which to pick out images thought to appeal to each of the four groups. This would allow us to have a larger positive annotation rate than if images were just randomly sampled from the Facebook images dataset. 

[1] Fitzsimons, T. (2018, November 08). Record LGBT support for Democrats in midterms, NBC News Exit Poll shows. NBC News. Retrieved from https://www.nbcnews.com/feature/nbc-out/record-lgbt-support-democrats-midterms-nbc-news-exit-poll-shows-n934211.

[2] “Wide Gender Gap, Growing Educational Divide in Voters’ Party Identification.” Pew Research Center, Washington, D.C. (2018, March 20) https://www.people-press.org/2018/03/20/wide-gender-gap-growing-educational-divide-in-voters-party-identification/. 

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

1. In order to connect to the Case Western Reserve Univeristy High Performance Computing (Case HPC), one must first have a Case account or an affiliate account. Information about eligibility and requesting an affiliate account can be found [here](https://case.edu/utech/help/knowledge-base/affiliate-network-id).
2. Set up [two-factor authentification](https://webapps.case.edu/duo/webauth.py) through Case using Duo. The easiest authentification method is a push notification sent to your phone by downloading the Duo Mobile app.  
3. Install the [Case FortiClient VPN](https://case.edu/utech/help/forticlient-vpn) (Virtual Private Network), which will allow you to connect to Case Western Reserve University network remotely. Once FortiClient has been installed on your computer, run the VPN; you will need to use Duo two-factor authentification first. 
4. Once connected to the Case network, open the terminal and ssh into the HPC by ```ssh <CASE id>@rider.case.edu```. When prompted, enter the password for your Case [affiliate] account ```<CASE id>@rider.case.edu's password: <enter CASE password here>```. Upon seeing ```[<CASE id>@hpc3 ~]$``` at the command line, you have successfully logged into the HPC!
5. Executing ```pwd``` should show that you are in your home directory ```/home/<CASE id>```. To change directory to Red Hen's server, execute ```cd /mnt/rds/redhen```.
