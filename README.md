# CI-CD-AWS-codepipeline-project
Practicing CI/CD hands on via AWS code pipeline. The guide will show how to create a simple pipeline that pulls code from a source repo (codecommit) and automatically deploys it to an AWS EC2 instance.


## Summary, Pre-requisites and Overview

* Creating a release pipeline that automates the software delivery process using AWS codepipeline.
* Connect to a source repository, such as AWS codecommit, Amazon S3, or Github to your pipeline.
* Automate code deployments by connecting your pipeline to AWS codeDeploy, a service that deploys code changes committed to your source rep to Amazon EC2 instances
* Optional: plug in a build service such as Jenkins

Tutorial: Create a simple pipeline (CodeCommit repository)
The pipeline has two stages:

* A source stage (Source) for your CodeCommit source action.
* A deployment stage (Deploy) for your CodeDeploy deployment action.

### Pre-reqs follow along here prior to it all:

https://docs.aws.amazon.com/codepipeline/latest/userguide/getting-started-codepipeline.html
I used a virtual machine as my “local machine”
Things to create prior to starting the project are above ^. But here are the basics:

* Create an IAM user. Set up the access keys, permissions for the user to use codecommit as in the tutorial
* Create and upload a public key from your local machine to AWS IAM console
* Create and Git credentials in IAM.
* Create a config file
* Create an empty Repo
* Download the zip files as instructed in the tutorial and add them into your local machine

## Testing git and ssh by pushing the local files to the new empty repo

***Quick pro tip: I had issues using ssh as the “clone url” e.g: ssh://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo***

***Instead use your SSH key ID as the user like ssh://ExamplekeyID@git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo***


### Pushing files/folders using GIT

Follow through the tutorial and you will successfully “push” the files and directory you downloaded to your local machine, to your empty repo.


