# EZ! GitHub Actions challange
![ez logo](/resources/images/ez/ez-smiley-small-logo.png)
## GitHub repository creation
creating a GitHub repository for the challange, based on a ready made project
 1. Login to your GitHub account. If you don't have a GitHub user yet, [sign up to GitHub](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account#signing-up-for-a-new-account).
 2. browse to the [Import your project to GitHub](https://github.com/new/import) page
 3. In the '**Your old repository's clone URL**' textbox, insert the following path:
  ```
  https://github.com/yorammi/ez-golang-example.git 
  ```
 3. In the '**Repository name**' textbox, name your repository as 'ez-dotnetcore-example' or whatever name you prefer
 7. in the '**Visibility Level**' field, select '**Private**' or '**Public**' - whatever you like.
 8. Click the '**Begin import**' button

## Adding workflow
1. Browse to your new created repository
2. Browse to 'Settings'/'Actions'/'General'
3. Select the 'Allow all actions and reusable workflows' option and click the 'Save' button
4. Select 'Actions' from the top toolbar
5. Select the 'Go' suggestion (if it is not listed, search for it') and click the 'configure' button
6. Click the 'Commit changes ...' button in the opened page
7. Click the 'Commit changes' in the pop up form
8. Browse to the 'Go' action to see that the build run and pass OK

## Advanced challange
If you like to get better in GitHub Actions, try to modify the yaml file so the flow will:
- Lint and vet the code (install and use golint for that)
- build the Dockerfile
- Upload the Docker image to Dockerhub
You can get inspiration from the flow that resides in the 'possible-challange-solution' branch


