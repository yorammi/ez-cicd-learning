# EZ! GitLab challange
![ez logo](/resources/images/ez/ez-smiley-small-logo.png)
## GitLab project creation
creating a GitLab project for the challange, based on a ready made project
 1. Login to your GitLab account. If you don't have a GitLab user yet, [sign up to GitLab](https://docs.gitlab.com/ee/user/profile/account/create_accounts.html#create-users-on-sign-in-page).
 2. click the '**New Project**' button
 3. Select the '**Import project**' option and click on it
 4. Click the '**Repository by URL**' option
 5. In the '**Git repository URL**' textbox, insert the following path:
  ```
  https://gitlab.com/ez-yorammi/ez-dotnetcore-example.git 
  ```
  6. in the '**Project name**' textbox, insert the following name, or whatever name you prefer:
  ```
  Ez Dotnetcore Example
  ```
 7. in the '**Visibility Level**' field, select '**Private**' or '**Public**' - whatever you like. 
 8. Click the '**Create project**' button

## General pipeline guidelines
The purpose of this challange is to create a CI/CD pipeline.

The syntax of the pipeline should be according to: https://docs.gitlab.com/ee/ci/yaml/.

In order to really understand the syntax, please don't use a template pipeline and don't use the ready-made solution which you can find as a project branch.

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
