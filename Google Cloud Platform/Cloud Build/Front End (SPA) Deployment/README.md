# About
These all configuration files is use when we want to deploy front end application that build using SPA framework such as Vue.js, React.js, Angular.js, etc, on Google Cloud Platform (GCP) using Google Cloud Run service.
Make sure you put all these configuration files in root folder of the project.
Also, you have to create cloud build trigger on google cloud console, so the deployment process will be automatically triggered when you push the changes to the branch of Git Repository.
These are some files in this folder:
- [nginx.conf](nginx.conf) file is used for configure nginx image that will be used for storing bundled project of SPA.
- [Dockerfile](Dockerfile) is used for configure our docker image.
- [cloudbuild.yaml](cloudbuild.yaml) file is used for triggering cloud build on Google Cloud console. The name of this file is depends on your configuration of cloud build trigger. But, the default is `cloudbuild.yaml`.

Please read all the comments on each respective file carefully before you use all these configuration file. Edit based on your own needs.