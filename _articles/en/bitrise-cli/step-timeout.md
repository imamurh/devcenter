---
title: Setting a time limit for steps
tag:
- cli
- steps
summary: Ensure that your builds do not exceed the time limit by setting up step timeout
  for steps that might cause builds to hang.
redirect_from: []
menu:
  bitrise-cli-main:
    weight: 25

---
Ensure that your builds do not exceed the time limit by setting up step timeout for steps that might cause builds to hang.

A step timeout, defined in seconds, sets a maximum time a step is allowed to run. If the step exceeds that limit, the workflow moves on to the next step. This is useful if, for example, your builds hang for not immediately obvious reasons - you can set timeouts for the step or steps which are suspected to have caused the problem.

1. Find the step in the `bitrise.yml` file.

   Don't forget you can edit the `bitrise.yml` file of your project on [bitrise.io](https://www.bitrise.io): open the `Apps` page, select your app, click the `Workflow Editor` tab then click `bitrise.yml`.
2. Add a `timeout` property before the other step inputs.

**Example**:

``` yaml
- xcode-test@1.18.14:
     timeout: 120
     inputs:
     - project_path: "$BITRISE_PROJECT_PATH"
     - scheme: "$BITRISE_SCHEME"
```

And you're done! In our example, the `xcode-test` step will abort after 120 seconds. Check the build logs to see what caused the step to exceed the limit.

<div class="banner">
	<img src="/assets/images/banner-bg-888x170.png" style="border: none;">
	<div class="deploy-text">Now you know everything</div>
	<a target="_blank" href="https://app.bitrise.io/dashboard/builds"><button class="button">Go to Bitrise now</button></a>
</div>