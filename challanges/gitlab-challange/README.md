# EZ! GitLab challange
![ez logo](/resources/images/ez/ez-logo-small.png)
## GitLab project creation
creating a GitLab project for the challange, based on a ready made project
 1. Login to your GitLab account
 2. click the '**New Project**' button
 3. Select the '**Import project**' option and click on it
 4. Click the '**Repository by URL**' option
 5. In the '**Git repository URL**' textbox, insert the following path:
  ```
  https://gitlab.com/ez-yorammi/ez-dotnetcore-example.git 
  ```
  6. in the '**Project name**' textbox, insert the following name, or whatever name you prefer (remember that this project will be used for all the rest of the labs as well):
  ```
  Ez Dotnetcore Example
  ```
 7. in the '**Visibility Level**' field, select '**Internal**'
 8. Click the '**Create project**' button

## General pipeline guidelines
The purpose of this lab is to create a CI/CD pipeline for the master branch of the project that you've created on Lab02.

The syntax of the pipeline should be according to: https://docs.gitlab.com/ee/ci/yaml/.

In order to really understand the syntax, please don't use a template pipeline and don't use the ready-made solution which you can find in the project branch which its name matches the name of the lab.

For creating a first CI/CD pipeline, or updating it, you can just click the 'CI/CD' option on the left pane, and then click the 'Editor' sub-item.
Then, make sure you select the correct branch on the top drop-down list.

If the branch doesn't have a pipeline yet, click the 'Configure pipeline' button. You can use the template pipeline for your needs. 

## 'build' stage

Create a pipeline with only one stage for 'build'.
The stage should have those commands:
```
dotnet restore
dotnet build -c Release
```

in addition, the stage should archive the following:
```
./**/dotnetcore-sample.dll
```
which should expire in 1 day.

## 'test' stage

Add a 'test' stage to the pipeline.
The stage should have this command:
```
dotnet test -c Release
```

## 'deploy' stage

Add a 'deploy' stage to the pipeline.
The stage should have this command:
```
dotnet publish -c Release -o /app
```

in addition, the stage should be set with an **environment** called **production**.
