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

Example after a successful "git push"
https://github.com/Darthstevo/CI-CD-AWS-codepipeline-project/blob/main/Example-git-push

## Create an EC2 Linux instance and install the codeDeploy agent
* Create a role, attache the code deploy permissions to this role
* Create an instance
* Attach your new role
* Set up security groups ( remember if you only use your IP as source, it will only show for that ip device. Can use 0.0.0.0/0 for testing)
* Add boot script (code deploy agent) to the new instance:
Bootscript here: https://github.com/Darthstevo/CI-CD-AWS-codepipeline-project/blob/main/codedeploy-bootscript

## Create an Application in CodeDeploy
* Create a role for CodeDeploy
* Create an application on CodeDeploy
* Create a Deployment Group

## Create your first Pipeline in CodePipeline
* In this step, you create a pipeline that runs automatically when code is pushed to your Codecommit repo.
* The pipeline starts running after it is created. It downloads the code from your CodeCommit repository and creates a CodeDeploy deployment to your EC2 instance. * You can view progress and success and failure messages as the CodePipeline sample deploys the webpage to the Amazon EC2 instance in the CodeDeploy deployment.
* You can view the pipeline now

**Note:** Mine failed due to the scripts having different extensions at the end. It's fixed via yml file.
But the issue is, why isn't my repo being updated when i git push? Even though it says “everything up to date” it does not update my codecommit repo.

**In case you see the following errors**

when trying to push my repo branch:

*“does not appear to be a git repository
fatal: Could not read from remote repository. “*

**Fix:** Be sure to edit the file first so git can see that something has been changed. 
* Then do:
* git add <yourfile>
* git commit -m “updating file”  (or whatever you want to say)
* Git push
* Ref: https://docs.aws.amazon.com/codecommit/latest/userguide/how-to-create-commit.html


