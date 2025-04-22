# Welcome to the de.KCD summer school 2024: Deploying Large Language Models in the cloud


Ever wanted to look behind the – technical and organizational – scenes of large language models? Already have your own AI research project sketched out but unsure of how to actually get started? Looking for cloud storage to power up your LLM but getting caught up in regulatory requirements?

This summer school will provide practical answers by working with you on your own hands-on sample LLM in the [de.NBI cloud](https://www.denbi.de/cloud). It is part of the [de.KCD](https://datenkompetenz.cloud/) project which aims to systematize and share the unique competence and knowledge of the de.NBI community – e.g., with regard to difficult topics such as handling sensitive data – across different sites and disciplines. Instead of struggling through the steps on your own and reinventing the AI wheel over and over again, we aim to pool our joint expertise and provide you with a shared, tried-and-tested workflow for cutting-edge research.

Over the course of the week, we will walk you through the entire lifecycle of LLM deployment in the cloud. We will take a deep dive into the individual stages of the “day zero one two operation” concept of software engineering – where day 0 is the planning and design phase (including setting up your cloud access and drafting your data management plan), day 1 is go-live (installing and deploying your LLM), and day 2 is continuous operations (including backups and user authentication).

>[!TIP]
>GitHub has a Discussions function/page (https://github.com/llmcloud24/de.KCD-Summer-School-2024/discussions), so feel free to use that as well!
>We will check and address your issues or suggestions there!


## Important Links 

* TESS: https://tess.elixir-europe.org/events/de-kcd-summer-school-2024-deploying-llms-in-the-cloud 
* Schedule: https://llmcloud24.github.io/schedule.html  
* Github : https://github.com/llmcloud24/de.KCD-Summer-School-2024
* DeNBI cloud: https://signup.aai.lifescience-ri.eu/fed/registrar/?vo=denbi&group=LLMcloud24  
* DeNBI cloud wiki: https://cloud.denbi.de/wiki/Compute_Center/Berlin

 ### Trainers

- **Dr. Sebastian Lobentanzer:** Uni Heidelberg – Biomedical researcher and developer of [BioChatter](https://biochatter.org/)
- **Prof. Dr. Fabian Praßer:** Berlin Institute of Health @ Charité – Head of [Medical Informatics Group](https://www.bihealth.org/en/research/research-group/prasser-lab-medical-informatics)
- **Dr. Jeanne Wilbrandt:** Leibniz Institute on Aging – Fritz Lipmann Institute –  [Data Steward](https://www.leibniz-fli.de/research/good-scientific-practice/data-steward-at-fli)
- **Martin Braun:** Berlin Institute of Health @ Charité – Developer at the [Research Group Cloud & IT](https://www.hidih.org/research/health-data)
- **Jakob Mathis:** Berlin Institute of Health @ Charité – Systems Administrator [Cloud & IT](https://www.hidih.org/research/health-data)
- **Foo Wei Ten:** Berlin Institute of Health @ Charité – Systems Administrator [Cloud & IT](https://www.hidih.org/research/health-data)
- **Lisa Schaak:** Berlin Institute of Health @ Charité - Technical Writer [Cloud & IT](https://www.hidih.org/research/health-data)

### Participants

**Target audience:** Everyone interested in digging into the technical and organizational details of deploying large language models for research via cloud infrastructure. Most of our trainers come from a biomedical and IT background. However, we are looking forward to an interdisciplinary exchange with research-developers and developer-researchers from all kinds of academic disciplines.

**Prerequisites:**  In order to be able to follow the practical exercises, you will need at least basic terminal knowledge. Some experience with programming languages - ideally python, but R, perl, SQL etc. are also fine - and basic knowledge of docker is recommended. We will provide detailed step-by-step instructions in writing throughout and after the workshop.

**Learning goals:** Participants will deploy their own LLM in the de.NBI cloud via a step-by-step guided journey throughout an entire lifecycle from design via deployment to productive operation.

### Setup

For the original Summer School we set up an openstack project at the Berlin node of the de.NBI cloud, this project was deleted after the end of the Summer School. To follow on your own, you (resp. your PI) need to register and apply for a new project at the de.NBI cloud:
- Registration for de.NBI: [https://cloud.denbi.de/wiki/registration/](https://cloud.denbi.de/wiki/registration/)
-  Application for a project: ([https://cloud.denbi.de/wiki/portal/allocation/](https://cloud.denbi.de/wiki/portal/allocation/))
-  Quota: for each participant we recommend at least "de.NBI mini" image (16 GB RAM and 8 CPUs)
-  Note for trainers: We recommend making sure the vms can be created, ssh works, connection works in the vms, docker works, etc. beforehand and get some external users to check, since things might be different in different locations and project.


## Program

### [Day 1: Monday, September 16 - How to Cloud](https://github.com/llmcloud24/de.KCD-Summer-School-2024/tree/main/Day_1)

Getting to know the de.NBI Cloud and each other: celebrating interdisciplinary and technological progress. Take a deep dive into access, roles and requirements and learn more about the project idea. 

[09:00 - 10:00] Check-in & help with technical set-up  
[10:00 – 11:00] Introduction (Lisa Schaak)  
[11:00 - 12:00] de.NBI Cloud (Martin Braun, Jakob Mathis)  
[12:00 – 13:00] Lunch Break  
[13:00 – 15:00] de.NBI Cloud continued (Martin Braun, Jakob Mathis)  

  
### [Day 2: Tuesday, September 17 - How to Data](https://github.com/llmcloud24/de.KCD-Summer-School-2024/tree/main/Day_2)

Before we can get the data to work for us, we need to work for the data: draft a data management plan, record all processing activities in accordance with the EU-GDPR, ensure IT-security and ethically sound and unbiased FAIR data.
  
[10:00 – 11:00] Data Protection (Fabian Praßer)  
[11:00 - 12:00] Data Management I (Jeanne Wilbrandt)  
[12:00 – 13:00] Lunch Break  
[13:00 – 14:00] Data Management II (Jeanne Wilbrandt)  
[14:00 - 15:00] Data Ethics (Lisa Schaak)  


  
### [Day 3: Wednesday, September 18 - How to LLM](https://github.com/llmcloud24/de.KCD-Summer-School-2024/tree/main/Day_3)

 Now we are finally ready for the long awaited action: today we will be deploying our own LLM in the de.NBI cloud. Learn all the practical ins and outs of generative AI and transformer architecture. And see all our planning efforts from the previous days come to fruition.

[10:00 – 12:00] LLM Deployment I (Sebastian Lobentanzer)  
[12:00 – 13:00] Lunch Break  
[13:00 – 15:00] LLM Deployment II (Sebastian Lobentanzer)  


### [Day 4: Thursday, September 19 - How to Service](https://github.com/llmcloud24/de.KCD-Summer-School-2024/tree/main/Day_4)
  
We are live – but for how long? Today we will take another deep dive into the technical details – such as Let’s Encrypt certificates, reverse proxy, user authentication and backup – that are fundamental to keeping our service up and running.

[10:00 - 12:00] Operations I (Martin Braun, Jakob Mathis, Foo Wei Ten)  
[12:00 - 13:00] Lunch Break  
[13:00 - 15:00] Operations II (Martin Braun, Jakob Mathis, Foo Wei Ten)  

### [Day 5: Friday, September 20 - How to Success](https://github.com/llmcloud24/de.KCD-Summer-School-2024/tree/main/Day_5)
   
You've made it! Today we will be wrapping up our week's work: we will reserve some time for self-study and Q&As to complete your hands-on examples. We will also look at some real-life examples and discuss the associated successes and challenges.

[10:00 - 11:00] Wrap-up Discussion (Lisa Schaak)  
[11:00 - 13:00] Guided Self-Study (Martin Braun)  

<p xmlns:cc="http://creativecommons.org/ns#" >This work is licensed under <a href="https://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC BY 4.0<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1" alt=""></a></p>

