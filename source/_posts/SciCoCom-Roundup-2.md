---
layout: posts
title: Science Coding Conference 2017 Roundup - Day 2
date: 2017-08-02 13:39:19
tags: Conference
---
# Alys Brett - Research Software Engineers
Day 2 started with an experiment - a keynote address from someone on the other side of the world.
Alys Brett is from the Culham Centre for Fusion Energy in Abingdon, Oxfordshire, England. She is a Software Team leader and Joint Chair of UK Research Software Engineer Association [RSEA](http://rse.ac.uk/)

Rather than risk the entire talk to the Zoom video conferencing system Alys recorded a video of the main part of her talk which we played to the audience, followed by a live Q&A through the conferencing system. This worked well - perhaps everyone should record their presentations.

At Culham Alys has been collaborating on research code for the Fusion Energy Joint European Torus (JET) Data pipeline. This includes stages of:
* Store raw data
* Processing
* Discovery
* Access - via API to abstract away underlying storage
* Analysis
* Visualise

Research software (like most other) has these goals:
* Reusable
* Readable
* Reliable

Within the research organisation there can be structural and cultural barriers to good software engineering - for example whose job is it to focus on quality when career structure and research metrics actively penalise researchers who spend time on code quality.

Introducing the Research Software Engineer (RSE) someone who combines SE skills with research skills.

They can be found in:
* Research IT depts
* HPC centres
* National labs and large facilities
* or can simply be the post-doc everyone turns to for help.

One difficulty can be recognising the role for example in a recent survey of  10,000 academic jobs advertised in the UK they found about 400 were software related or had a software development component. That's good - but they also found 194 different job titles!

### A brief history:
* 2010 - Software sustainability institute. - 4 uk unis, better software, better research
* 2014 - UK RSE association founded.  Community to represent. Elected Committee.
* 2015 - UK Funding agency, Dedicated RSE fellowships. Designed to kickstart establishiment of RSE software groups.  7 awarded.  Growth to 800 members. Employed a part time coordinator, created an RSE leaders forum to share knowledge and experience.
* 2016 - first RSE Conference. Current committee elected at the conference. Created a new website http://rse.ac.uk/ and slack channels. http://rse.ac.uk/slack/

### What do RSEs do?
* Advising on tech
* Architecture and co-design
* Refactoring
* Optimising and performance
* Porting
* Scaling, cloud HPC
* Workflows and dev practices
* Advising on project structure
* Enabling open science - reproducibility

### Skills
* Communication
* Programming
* Bridget between groups.
* Technical software
* Patience

### Problems
* Only 11% RSE female. In UK most RSEs come from Physics & Math backgrounds which is male skewed. Care is needed in job descriptions to avoid implicit bias.
* 'Bus Factor' => how many developers have to be hit by a bus before a project fails. In a survey they found that 46% of projects had bus factor of 1, that is a single person working on the project.

### Future Growth:
* There are now RSE orgs in [Germany](http://de-rse.org) and the [Netherlands](http://nl-rse.org)
* There is talk of a NZ and AU organisation and Aleksandra Pawlik at NeSI is working with the start-up group.

### Q&A comments and observations:
* WRT low bus factors: Many SE techniques are designed to limit the risk. Defence comes from pair programming, peer review, code repositories, automated test, while standard build and deployment tools across projects help new developers to pick up a project quickly.
* Career paths for RSEs. Are there groups trying to define a career structure? - where to go after RSE?  will there be a Research BA or Research Systems Architect?
* Interested in the reward patterns for these roles. is there a credit taxonomy or recognition metrics? Currently to get recognition of contribution to research projects one has to write paper about the software and get cited, but would be better to get Software and Data to be first class research products.
* RSE tend to have a generalist mindset, there is commonly an ability to balance - not wanting to be hard core academics or pure software engineers.


# Finlay Thompson - Dragonfly data science
Finlay introduced us to Stencila. https://stenci.la/. a client application that works like a word processor but allows the inclusion of code and data to generate interactive and interrogatable documents. This is similar in some ways to Jupyter notebooks but the focus is more towards a document with live code than an annotated program.

Stencila was created to make it easier to collaborate between coders and clickers. The focus on supporting reproducible research.

It is based on an underling text document format (markdown) with visual javscript editor (think Atom) that  contains embedded code and data blocks, which can be executed dynamically against a range of language backends. e.g R + Python. The system uses dockerfiles to generate the server back end.

Created by [Nokome Bentley](https://www.linkedin.com/in/nokomebentley/) here in NZ, has been funded by the Alfred P Sloan foundation and is now supported by developer teams around the world.

SE Essentials
* Version control used properly, branches, pulls, code reviews, tags etc.
* CI all the time, no builds/deploys without VCS
* Tagged builds intrinsically reproducible at any date.
* Enhances collaboration and report writing context.
* Containerisation.  Docker use systematically everywhere.

Example:
Python library - nzelect, nzcensus. On github
https://github.com/ellisp/nzelect

DockerFile - Software Environment as Code.
Stencila/alpha - full dev environment.

Coder writes docker file to contain all the code data and libraries.
Containerise.
Write presentation documents

Install upstream libraries in the dockerfile. Author needs to build dockerfile on their computer and upload then CI system will build docker image.

I think that this type of application absolutely requires secure containers running at the back end otherwise each editor instance becomes a great way to deliver remote code execution code on your server. :)

# First steps in creating 3D Vis using Python & VTK - Alexander Pletzer, NeSI

Code for this demo at https://github.com/pletzer/firstStepsInViz
There's not much to say - go work through the demo and examples and have some fun with 3D models plotting data.

# Creating the chaotic sandpit, giving corporate IT the right tools and freedom to support science. - Jonathon Flutey, (Johnny) Victoria University, Wellington

Traditional core IT has key drivers of stability and security along with limited resources. This tends to result in systems that are locked down, not flexible, and not available when needed.

Victoria Uni created a [Vision and strategy for Digital learning and Teaching 2012 to 2017](https://www.google.co.nz/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0ahUKEwi5ydXExLrVAhUBLJQKHZ0PDxEQFgglMAA&url=http%3A%2F%2Fwww.victoria.ac.nz%2Flearning-teaching%2Fpartnership%2Ftechnology%2Fdigital-vision-strategy.pdf&usg=AFQjCNEwiSvAW0DVQz6VoFJ_n9Qas4Hlmw)

They measured themselves against a Maturity Model:
* Mobility
* Support
* Data
* Policy
* Processes
* Tools
* Collaboration
* Computational
to identify weak points.

They developed an IT / Researcher engagement strategy:
* Hire in disciplinary knowledge - digital humanities, research knowledge
* Embed staff inside the research lifecycle and understand the process
* React - on demand as soon as possible, delays stop research
* Hire staff not tied to ITS architecture, services, support or policy - especially security.
* PD you can do whatever you want - trust the tech

Which led to the recruitment of staff like Andre who have the time and role to sit and work with researchers to identify and deliver their technology tools and processes while bringing in best practices.

They identified three levels of platform sophistication and formality:
* Chaotic Sandpit:
  * On demand, breakable, anything goes, no security or architecture
	* Unrestricted
	* Isolated from important systems
	* Not very supported - If something stops working the IT pager doesn't have to go off.
	* Researcher led - some technology understanding
	* AWS, Azure, Catalyst Cloud, Docker
	* Prototype, Proof of concept, testing, hacking,
	* available in hours, short life cycle - shorter than OS patch cycles.

* Humming Hothouse
  * Evaluation, assessment, pilot, transitioning
  * collaboration between research and formal IT
  * AWS, Azure, Catalyst Cloud, Docker, private cloud
  * live testing, scaling up, persistent storage, privacy
  * available in days, months life cycle - project scale
  * Experimental
  * But may have privacy and security concerns so more care required

* Disciplined Engineroom
  * formal delivery teams
  * ITIL
  * external support, licenced software
  * commercialisation
  * SLAs
  * Azure, VMWare, Physical SOE servers
  * security
  * built for production - weeks?
  * long term persistence

May need to put containers into long term digital preservation system.

# Introduction to International Image Interoperability Framework IIIF - Bruno  Kinoshita. NIWA
Everyone can get involved in Open Source projects. They are a good place to learn new code and techniques outside of the constraints of work. Bruno got involved in the IIIF project after a pub conversation.

Website: http://iiif.io/
Github: https://github.com/iiif

## What is IIIF?
* A Group of standards for sharing and reusing images
* very high res images
* Metadata enriched images
* Supports Annotations and linked data
* Search tools

Think Google Map tiles rather than PNG files.

## Features:
* really large images with deep zoom capability
* select by URL region of interest, rotation, quality etc.
* can cite annotate & share subsets of the image.
* supports user authentication for access control
* open standard - avoid vendor lock-in
* allows combining content across multiple repositories
* on the fly thumbnails

### Implementations:
* [Cantaloupe](https://medusa-project.github.io/cantaloupe/) - java
* [Loris](https://github.com/loris-imageserver/loris) - Python
* [IIPImage](http://iipimage.sourceforge.net/) - C++
* [Go-iiif](https://thisisaaronland.github.io/go-iiif/) - Go

Follow Bruno on twitter at @kinow


# Applying good software engineering techniques to optimising HPC code. - Chris Scott
In another example of the NeSI consultancy services Chris Scott talked about how some simple optimisations to a complex computational model resulted in significant performance improvements.

Model [TopNet](http://tools.envirolink.govt.nz/dsss/topnet-/) is a catchment water-balance calculator. By running profiling tools on the system Chris was able to identify some key bottleneck in writing checkpoint files out to NetCDF files on disk. By re-writing to move from line by line writes to larger blocks the bottleneck went away along with the pain the system was causing the HPC disk subsystems.

This was not a particularly complex optimisation the key there is simply having access to someone who can focus on the how a thing runs - rather than the researcher who focuses on the internal logic. By adding tests and profiling tools it becomes easier not only to improve the performance but to help the researchers avoid future such bottlenecks.


# Closing
Nick Jones from NeSI gave a glimpse of what's coming soon for NZ researchers and developers in the form of new supercomputers. Rather than repeat it here take a look at https://www.nesi.org.nz/news/2017/06/new-computing-platform-power-nz-research

Finally I closed the conference with a brief summary of the above and some new things I needed to go home and investigate:
New terms
* Semantic versioning
* Open annotation
* www.dot.tk. Free domain names for all.
* Bus Factor
* SciDevOps
* and a list of github repos to fork.

After a show of hands it looks like everyone enjoyed their time at the conference, made new friends and learned new stuff. They want to do it again, so do I so we will be back next year with SciCoCon 2018. or perhaps the first NZ RSEA conference.
