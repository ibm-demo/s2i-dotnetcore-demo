# Building an example .NET Core application within OpenShift

## Pre-requiste

### Source control

1. Sign up or login to [GitHub](https://github.com)
2. Navigate to [s2i-dotnetcore-ex](https://github.com/redhat-developer/s2i-dotnetcore-ex)
3. Click on fork ![fork](images/fork.png)
4. Select account to fork ![select](images/fork-select.png)
5. Copy and keep the GitHub repo url for later ![copy-git-address.png](images/copy-git-address.png)

## Prepare OpenShift playground

1. Navigate to [OpenShift Interactive Learning Portal](https://learn.openshift.com/)![openshift-learning-portal](images/openshift-learning-portal.png)
2. Click on start course under OpenShift playgrounds
3. Click on start scenario under [OpenShift 3.11 Playground](https://learn.openshift.com/playgrounds/openshift311/)![openshift-311-playground-start](images/openshift-311-playground-start.png)
4. Click on start scenario. The playground will be available for 60 minutes after which time it will be destroyed.

## OpenShift Playground

1. Follow the instructions to log in to the cluster ![login-openshift](images/login-openshift.png)
2. Do not click on continue until lab is completed
3. Click on dashboard to launch OpenShift console ![login-openshift](images/login-openshift.png)
4. Login using the provided credentials `developer`/`developer` ![console-login](images/console-login.png)

## Build and deploy .Net Core application

1. On the catalog page, click on `.NET Core Example` ![click-dotnetcore-example](images/click-dotnetcore-example.png)
2. Click next ![dotnetcore-1](images/dotnetcore-1.png)
3. Select `Add to Project` as `myproject`![images/dotnetcore-3](images/dotnetcore-3.png)
4. Change `.NET builder` to `dotnet:2.0`
5. Change the `Git Repository URL` to the repository created earlier.
6. Change `Git Reference` to `dotnetcore-2.0` ![images/dotnetcore-4](images/dotnetcore-4.png)
7. Click `Next`
8. Click `Complete` ![images/dotnetcore-5](images/dotnetcore-5.png)
9. Click `Continue to the project overview` ![images/dotnetcore-6](images/dotnetcore-6.png)
10. Click on build name `dotnet-example` to access the build page![images/dotnetcore-build1](images/dotnetcore-build1.png)
11. Click on the build number `dotnet-example` ![images/dotnetcore-build2](images/dotnetcore-build2.png)
12. Explore the build details, environments, logs ![dotnetcore-build3](/images/dotnetcore-build3.png) If required, manual build can be triggered by clicking on `Start Build`

## Accessing the deployed application

1. Click on overview
2. Click on routes URL to access the deployed application ![dotnetcore-routes-1](images/dotnetcore-routes-1.png)

## Add GitHub

1. Click on `Builds` -> `dotnet-example`, then click on configuration ![dotnetcore-git-webhook-1](images/dotnetcore-git-webhook-1.png)
2. Click on copy button to copy the webhook url. Keep for reference
3. Navigate to the GitHub repository URL you forked earlier. Click on settings. ![dotnetcore-git-webhook-2](images/dotnetcore-git-webhook-2.png)
4. Click on `Webhooks` and then click on `Add Webook` ![dotnetcore-git-webhook-3](images/dotnetcore-git-webhook-3.png) You might be asked to verify your GitHub credentials.
5. Change the `Payload URL` to the `GitHub Webhook URL:` copied earlier. Disable `SSL Verification`(Not recommended but we are only doing a demo). For Events, select `Send me everything.` Click on `Add Webhook` to finish the process. ![dotnetcore-git-webhook-4](images/dotnetcore-git-webhook-4.png)

## Trigger a build

1. Navigate to the GitHub repository. Change the branch to `dotnetcore-2.0`. This is the branch we selected for the build. ![dotnetcore-github-1](images/dotnetcore-github-1.png)
2. Select folder `app` / `Views` / `home`. Click on `Index.cshtml` ![dotnetcore-github-2](images/dotnetcore-github-2.png)
3. Click on edit and make some changes to the text. Use your imagination or just add `Hello World`. ![dotnetcore-github-3](images/dotnetcore-github-3.png)
4. When happy with your changes, scroll to the bottom of the screen and click `Commit changes` ![dotnetcore-github-4](images/dotnetcore-github-4.png)
5. You have just make your first changes. Return to OpenShift console and check if a build is triggered automatically.

This marks the end of this lab.
