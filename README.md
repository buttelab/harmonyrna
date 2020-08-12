# HarmonyRNA Documentation

This is an overview of the HarmonyRNA project. This documentation is for researchers who intend to develop the project further. HarmonyRNA is a web tool for harmonizing RNA-Seq data in TPM and counts format. This documentation provides an introduction to the project and then gives instructions on how to code your own version of HarmonyRNA.

## HarmonyRNA Resources

* [Website](http://harmonyrna.ucsf.edu/): This is the HarmonyRNA website. This documentation explains how this website is built so that researchers and programmers  can build their own version of HarmonyRNA.
* [Video Tutorial](https://youtu.be/lm3t6yaIlV8): This video tutorial is a beginners overview of what HarmonyRNA is about and how to use it. Watching the video is the best way to begin learning about harmonyRNA. The video shows how to harmonize data steb-by-step using an example dataset.
* [Paper](https://drive.google.com/file/d/16xouMFAHRIXzRuIgKzalHpPLNAwJRUgS/view?usp=sharing): This is a preprint paper describing HarmonyRNA (to be published in Bioinformatics). Reading the paper is a good way to learn more about the purpose of 10k Immunomes. It also describes the novel TPM harmonization algorithm that was created for HarmonyRNA. You may also be interested in reading the [supplemental material](https://drive.google.com/file/d/1BjGXj2Do185-p6RNSwJMO4RS6djdJ4G1/view?usp=sharing).
* [Source Code](https://github.com/buttelab/harmonyrna): This github repo contains all of the source code. It's useful for scanning through the files, however, we **highly** reccomend using the dockerhub image when working on code. The README file that provides a thorough description of all source files.
* [Dockerhub](https://hub.docker.com/r/pupster90/combat-seq): This docker image is by far the easiest way to start working on the HarmonyRNA project. It contains a detailed step by step tutorial on how to get the website up and running, how to edit code, and how to publish final results to a shiny proxy server.
* [10k Immunomes Documentation](https://github.com/buttelab/10kimmunomes_v2): HarmonyRNA was used to harmonize data from the 10k Immuomes project. 10k Immunoms data is also the example dataset used in the tutorial video. To learn more about 10k Immuomes, you should read its documentation.

## Getting Started

The best way to get started is by learning to use HarmonyRNA as if you were a user. This way you undertand the purpose of the project. Briefly visit the website, then watch the tutorial video. Follow the steps in the video tutorial to harmonize the example dataset. After this, read the HarmonyRNA paper and supplmentary material to learn the basic architecture of the Harmony website and to learn the methodology behind its algorithm. Once these steps are done you can then move on to gain a deeper understanding of the code.

## Editing Code

HarmonyRNA source code is available on Github and Dockerhub. The README files on Github are a great place to learn about what the different files do in HarmonyRNA and where the best place is to start coding. However, please do not attempt to replicate HarmonyRNA by first cloning the Github repo. HarmonyRNA is an [R Shiny](https://shiny.rstudio.com/tutorial/) website with very specific settings and very specific packages installed. If you don't know what R shiny is, go through a few of the practice tutorials on their official site. After that, go to the HarmonyRNA [dockerhub](https://www.docker.com/products/docker-hub#:~:text=Docker%20Hub%20is%20a%20hosted,push%20them%20to%20Docker%20Hub) and follow the steps there to launch an [R Shiny Server](https://shiny.rstudio.com/articles/shiny-server.html) where you can run HarmonyRNA locally. [Docker](https://docs.docker.com/get-started/) is a tool that allows you to launch little pre-set-up "mini computers" from your computer. With docker you can launch HarmonyRNA in minutes. This will save you weeks are work. 

If you are interested in the example datasets used in the HarmonyRNA tutorial and would like to learn more about them, you should start by reading through the `other_code` folder on Github. The datasets were originally created as part of the 10k Immunomes project so you may need to eventually read the 10k Immunomes documentation. 

## Source Code Summary

We provide a summary of all the source code. This repository consists of an `app.R` file and four folders consitsting of R code and csv files. 

* [app.R](https://github.com/buttelab/harmonyrna/blob/master/app.R) This one file contains all of the code used to build the HarmonyRNA website. It is by far the most important file in the repository and where you should start reading. `app.R` launches an R shiny server. If you are unfamiliar with R shiny, you should do [tutorials](https://shiny.rstudio.com/tutorial/) on the R shiny website before continuing. The `app.R` file's code is broken up into two major sections the UI and Server. The UI creates all of front the end elements of the website. The server section manages the backend code and manipulates the website interface in real-time.

* [www](https://github.com/buttelab/harmonyrna/tree/master/www) This folder contains the images, datasets, and ComBat-Seq R files that are used by the R Shiny website. The dataset in `www` is the example dataset for the video tutorial. The R files are the original files from the [Combat-Seq github](https://github.com/zhangyuqing/ComBat-seq) repo. The only R file that is used in the website is `helper.R` which contains helper functions for the main ComBat-Seq function. The ComBat-Seq function was rewritten in `app.R` to accomadate R shiny features.

* [other_code](https://github.com/buttelab/harmonyrna/tree/master/other_code) This folder contains all other R code that is not used by the HarmonyRNA website. This code was used to build the example dataset for the video tutorial as well as to test the validity of the HarmonyRNA TPM harmonization algorithm. This code was originally run in the same lcoation as the `app.R` file. If tou intend to run this code you should first move it back to that location. The `make_tpm_files` and `make_unharmonized_tpm` use/create the data from the `tpm_data` and `test_data` folders.

* [test_data](https://github.com/buttelab/harmonyrna/tree/master/test_data) This is the raw counts/TPM data that is processed by the code in `other_code` to create the example dataset for the video tutorial. These raw counts/TPM files are themselves processed files from raw data collected from [immport](https://immport.org). If you would like to learn more about the datasets in this folder please read the [10k Immunomes Documentation](https://github.com/buttelab/10kimmunomes_v2)

* [tpm_data](https://github.com/buttelab/harmonyrna/tree/master/tpm_data) This data is the TPM files that are used in the video tutorial. These datasets were also used to build to whole blood reference dataset on [10k Immunomes](https://10kimmunomes.ucsf.edu/). The datasets were harmonzied together using the HarmonyRNA website. The [paper](https://drive.google.com/file/d/16xouMFAHRIXzRuIgKzalHpPLNAwJRUgS/view?usp=sharing) describes in more detail how and why this was done.

## Help and Contact

If you are another lab interested in HarmonyRNA, we are happy to have you reach out to [Atul Butte's lab](https://buttelab.ucsf.edu/). Sanchita Bhattacharya is the senior scientist and manager of this project (email: Sanchita.Bhattacharya@ucsf.edu). If you are a programmer with technical questions please reach out to the senior programmer of HarmonyRNA, Matthew Elliott (email: melliot1@ucsc.edu). We look forward to hearing from you!

