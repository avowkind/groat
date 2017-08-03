---
title: Science Coding Conference 2017 Roundup - Day 1
date: 2017-08-02 13:40:00
tags: Conference
---

On 1st & 2nd August 2017 over 50 Researchers and Software developers from Crown Research Institutes, Universities and Government agencies gathered together in Wellington for the second CRI Coding Conference - now renamed the NZ Science Coding Conference.

I'm Andrew Watkins and as General Manager of IT for NIWA and previous systems development manager it was my privilege to work with NeSI last year to create the first of these conferences. I felt that there was a real need to create a forum where the full range of software development activities that take place within science organisations could be represented and where we could promote high quality software engineering practices and tools to researchers and scientists who code.

This blog post is based on my closing speech at the conference and is a quick roundup of some of what we saw and learned.

Thanks to the organisers: Aleksandra, Rhiannon, Georgina from NeSI without whose planning and encouragement the event would not have happened. Also to Matthew Laurenson, Craig Stanton and others on the programme committee for selecting the presentations. We had an interesting mix of how-to technology, strategy and problem solving.

Thanks to NeSI for underwriting and to Victoria University for hosting.

# Peter Ellis
The day 1 keynote speech came from Peter Ellis - Currently at StatsNZ but until recently at MBIE.

Peter talked about the strategy and work involved in migrating the MBIE analytics teams from a point and click or MS Excel world to a code based environment, and then how they went on to build new higher level point and click tools. The overarching goal being to make accurate evidence available to policy makers, ministers & journalists.

Using Plato's cave as an illustration Peter said "We are using science to try to understand what the reality is. But there is still a lot of illusion present."

Strategically Peter needed to do two things:
- Define what was good practice for high quality analytics team
- Build skills and capability

Some of the immediate challenges were :
- A lack of version control leading to difficulties in reproducibility
- A lack of access to information for example being able to build appropriate indexes in source databases
- Limited tool - e.g. spreadsheets.

There does exist a nominal pipeline for data analysis :
- Source Survey data and transactional databases from multiple sources
- processing and quality analysis - some domain specific
- leading to cleaned, weighted, concorded microdata.
- followed by aggregation
- and finally reporting and visualisation

However, each of these stages would be manual and difficult to repeat accurately. So for example when creating a complex analysis model in Excel they would need to pull together sector data and present it in a way that makes sense to the public. It could take 18 months to gather the data, clean it up and generate the reports. The final model could not be easily updated and lacked documentation. It consisted of up to 30 linked spreadsheets managed by multiple different groups.

What was needed was a series of coding steps that aggregated the data and performed the analysis in a repeatable, revision controlled way so that updated reports could be generated whenever needed.

[Drew Conway Data science Venn diagram](http://drewconway.com/zia/2013/3/26/the-data-science-venn-diagram)

## Trends
Peter Identified some Sector Trends - these were confirmed by many of the speakers.
* Everything in code
* Reproducible - code, data and environments.
* Adaptive, using best in breed rather than big end to end Enterprise IT solutions
* Focus on software engineering processes - referencing Joels 12 point test for software teams
	* Version controlled
	* Modular
	* Peer review / pair programming
	* Continuous integration
	* Test led development & Automated Tests
	* Integrated documentation process.

Given that much of this type of software engineering improvements pay off in the long run with accuracy, reproducibility and maintenance gains they also needed to identify some quick wins. Their first project was for a tourism data improvement programme. Which bypassed traditional governmental data sources and went directly to commercial credit card and bank data, coupled with modern software techniques they were able to quickly generate excellent interactive visual reports for policy makers.

## Peter's keys to success:
* Build capability - both in data analysis teams and the wider researcher environment.
* Generate workplace specific development environments, provide access to the tools and data required.
* Use in house staff rather than external trainers. They are cheaper and the experience of training others is a valuable skill in its own right.
* Create an atmosphere of continuous learning, improvement and change.
* Don't wait to be perfect

# Whose who
In the second session we had representatives from the various organisations attending talk about their work and challenges.

Here are some of the common themes:
* Professional software development teams are often called in very late in a project - when the researcher has completed data capture and analysis and finally realises that they need to build an online tool or visualisation. By which time most of the funding has run out.
* There are often unreasonable expectations as to what operating an online system requires - such as assumption that a website once created can be left unmaintained and it will continue for the lifetime of the Internet.
* There was some discussion on the challenge of how to get in front of scientists and engage early. Ideas include:
  * Networking and teamwork conversations. Show up at the water cooler.
  * Proactive training for researchers. e.g. running software carpentry courses.
* Problem Valuing Skills
  * Science staff and professional IT staff have different incentives and performance metrics. Scientists may be measured on publications for example and time spent developing good quality code or effective tools may be undervalued.
	* Universities often use students and postgrads on development projects. This creates a built in high turnover making it difficult to maintain consistent development projects and code quality. There is an overhead of constantly retraining new staff and learning about the project.
	* A general undervaluing of the benefits of software engineering.
	* For all the talk of advanced technology a lot of benefit from moving up one step on the maturity model - e.g start using version control.
	* Some organisations are data rich but information poor, they have a multitude of data sets that are hard to discover, lack clear documentation and data models, lack processes and the means to analyse, and there is a lack of experienced data science capability.
* Legacy code & Silos
	 * Some organisations have very long running systems, e.g. Nationally Significant databases. These promote extreme conservatism and resistance to change. There is a requirement for long term statistics - whether for climate or job figures to be consistantly produced the same way each year.
   * Older systems have often evolved over time and have no as built description or design documentation.
* Labour costs massively outweigh compute equipment costs, yet the nature of IT budgets is that a researcher may have to work with a slow PC or wait weeks for access to online resources.
* How easy is it for scientists to
  * Use supporting infrastructure (e.g SQL noSQL
  * Get the right sized resource
  * Get to and use existing building blocks
  * Use infrastructure in research that is virtually identical to production

Automation and standard tools - lots more mentions of docker than last year.

# Talks and Presentations

## Hillary Oliver - Cylc
Hillary Oliver from NIWA told us about Workflow automation with Cylc. A major open source tool that manages complex workflows that have dependencies, spread over multiple servers, and include multiply periodic activities. Cylc was developed to manage environmental forecasting models on NIWA's HPC and is now used across the Unified Model consortium.

Written in Python, it uses a simple text based notation for generating workflows thus supporting revision control. A command line and API allow control of the workflow while it is in flight allowing users to start and stop processes, update dependencies and track progress, errors and success. It can even cope with entire servers being restarted in the middle of the workflow.

[See cylc.github.io](https://cylc.github.io/cylc/)

## Boosting R with Parallel Fortran and C. Wolfgang Hayek, NeSI/NIWA
Wolfgang talked about how NeSI makes available to researchers consultancy and support in optimising codes and helping systems make use of parallel processing capabilities.

The statistical programming language R is widely used in science across NZ. While it does support parallel programming through the parallel package this operates by spawning new processes for each thread. This approach takes time and extra compute resources and is disliked by HPC admins due to the high process count that results.

An alternative approach is to make use of R's ability to move code in to supporting C or Fortran libraries. By placing the parallel code into these libraries developers can make full use of tools such as OpenMPI to support multicore processors and OpenACC to support GPUs

The basic steps are:
* Identify compute intensive parts of the code using a profiler e.g. Rprof or callgrind.
* Identify compute intensive functions or loops with large trip count.
* moved these calculations to the external library.

In the example given moving just a few core routines into parallel libraries resulted in order of magnitude speed ups in model run times.

[NeSI consultancy services](https://www.nesi.org.nz/services/consultancy)

## An application of linear indexing to solve large combinatorial problems - Robbie Price, Landcare
Robbie introduced us to a fascinating corner of spatial analysis. Landcare works with many huge raster (gridded) data sets such as soil and land use maps. Typically these are manipulated within a GIS tool such as ArcGIS or QGIS.

One activity is combinatorial analysis a sort of 'SELECT DISTINCT' for raster data. While this function is available in GIS tools it may be limited to a certain number of layers e.g 20. While the data in question may have scores of layers.

Robbie worked in Python using the Anaconda suite and in particular GDAL and KEA.

Now I got a bit fuzzy on the details here but Robbie used a technique called Linear Indexing to effectively generate a constant time look up table for the combined raster data. This has the effect of reducing the data volume with no loss of fidelity and allows the analyst to answer simple questions about the data set - such as how many types of X are there, very quickly.

The new algorithm runs 100 times faster than the GIS algorithm and is now only limited in capacity by the characteristics of the storage file format.

## Research development and production of weather forecasts at MetService - Andy Zeigler, Met Service

Andy kicked off by talking about the phases of crafting research software:
* Experimental phase
  * exploratory and playful
* Development phase
  * stabilising and repeatable
* Operational phase
  * Scalable, updates never break
  * Accessible and it works continuously

There is a challenge for traditional IT groups operating in a research organisation in how best to both enabler for research and development as well as support sophisticated operational systems.

A big question is how easy is it for scientists to:
* make use of existing supporting infrastructure (e.g SQL noSQL databases),
* get access to the right sized resources - compute, storage etc.,
* get access to and make use of previously created building blocks - reuse,
* use infrastructure in research that is close to production systems in order to allow rapid productionisation of experimental systems.

In particular, given that labour costs, that is, scientist time, largely outweigh equipment and compute costs, what element of core productivity are we aiming to optimise - capital or time?

Producing good quality on-premise systems along with maintenance costs is slow and difficult. Problems multiply when systems require different versions of libraries, environments, platforms, and use different processes and conventions for creation and deployment.

By using common platforms and environments the cost and performance of production solutions can be predicted during the development phase.

MetService approach:
* Radical use of cloud platform as a service (PaaS) e.g. AWS.
* Give access to as much compute as required. that is to complete a model run scale out on many servers for a short time rather than run a few big servers for a long time. Optimise time to completion.
* give access to lots of other managed services e.g databases, load balancing, domains etc.
* Cost effective for research
* Scalable for production
* Low upfront cost
* Resilient around the world

* Use standardised language, package design and deployment patterns:
  * Subversion and GitHub
  * Peer review on merge to master
  * Python and conda
  * Julia and Docker
  * Jenkins CI/CD. Span from research to production.

* CI - Operational deployment
  * Triggered from tagged release
  * If build, test etc ok then pushed to prod
  * Shut down Jenkins every night, restart every morning.  Clean Setup.
  * Test complex software in parallel to production before switch.

  Don't nurse your infrastructure nurse your productivity and efficiency
  Nurse simplicity and repeatability for scale.
  Infrastructure is a means to optimise outcome.
  Select the right shoebox for your problem, not make your problem fit the box.

* Final thoughts
  * Automate, Automate, Automate, If you can't then don't think about using cloud
  * No one off experiments
  * Integrate roles Science, Development, Operations => SciDevOps
  * Infrastructure as code, software all the way down.

## DIY IT using AWS to support chaotic development and concepts - Andre Geldenhuis, Victoria University

Andre occupies a unique role at Victoria - a member of IT whose job it is to spend time sitting next to researchers and working to provide them with the technology tools they need to be productive.

In the demo Andre built a complete research sandbox in 20 minutes using AWS servers and ansible scripts to create a Jupyter Hub server complete with domain name and IP address.

Steps were:
* create an AWS small instance - Ubuntu server
* use Elastic IP to give it a fixed IP
* use www.dot.tk get a free domain name
* create SSL Cert to allow script access
* Ansible installed locally.

Then use the scripts at https://github.com/jupyterhub/jupyterhub-deploy-teaching
All the instructions are there.

The created system includes OAuth user authentication so you can control who gets access to the services.

I recommend starting at the github site and working through the instructions.
    **Note that you will end up using some paid for resources on AWS.**

## Modern Javascript Development, Scaffolding, Tools Testing - Uwe Duesing, NIWA :
Uwe demonstrated how modern languages and frameworks now typically come with tools that generate new projects according to best practices, that are setup ready to commit into git, deploy to servers, run auto tests etc.

This is a major shift from the days when many novices would create new projects based on template code abstracted from how-to's and tutorials. These projects often would be configured for simplicity and getting started rather than generating a production ready system.

Uwe demonstrated [Angular](https://angular.io/) in conjuction with a node.js package [Angular-cli](https://github.com/angular/angular-cli) a command line interface for generating and managing angular projects.

Although hampered rather by the VGA projector, Uwe was able to live demo installation of the tool chain and generation of a first project.  This project comes ready configure with end to end testing and unit testing capabilities so you can start writing fully tested applications from day one - by far the easiest way.

Again I recommend working through the readme to get a project started. Then perhaps watch [this course on youtube](https://youtu.be/htPYk6QxacQ) for a crash course in what a javascript framework can do for front end development.

The day ended with drinks, nibbles and socialising. 
