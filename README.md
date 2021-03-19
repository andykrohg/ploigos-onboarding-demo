## Apply a Greenfield app to ploigos
1. Clone this repository and cd into it:
    ```bash
    git clone https://github.com/andykrohg/ploigos-onboarding-demo.git
    cd ploigos-onboarding-demo
    ```
2. Generate a brand new application using the `quarkus-maven-plugin`:
    ```bash
    mvn io.quarkus:quarkus-maven-plugin:1.12.2.Final:create \
        -DprojectGroupId=org.acme \
        -DprojectArtifactId=getting-started \
        -DclassName="org.acme.getting.started.GreetingResource" \
        -Dpath="/hello"
    ```
3. Create the directory `cicd/ploigos-step-runner-config`, then copy sample configuration files into your project:
    ```bash
    mkdir -p getting-started/cicd/ploigos-step-runner-config

    cp Jenkinsfile getting-started/cicd/

    cp config.yml getting-started/cicd/ploigos-step-runner-config/

    cp sonar-project.properties getting-started/
    ```
4. Initialize `getting-started` as a git repository, then push to github (or wherever):
    ```bash
    cd getting-started
    git init -b main
    git add .
    git commit -m "Anchors away! ⚓"
    git remote add origin https://github/<your account>/getting-started.git
    git push origin main
    cd ..
    ```
5. (Optional) Create a fork of the [ploigos-cloud-resources-template](https://github.com/andykrohg/ploigos-cloud-resources-template), particularly if you'd like to update the name of the chart [here](https://github.com/andykrohg/ploigos-cloud-resources-template/blob/main/Chart.yaml#L2). Otherwise, your Kubernetes assets will have the default name `myapp`.
6. Replace line 10 of `tssc-pipeline.yml` with the URL for your `getting-started` repository (pushed in Step 4). If you created a fork of the helm repo in Step 5, replace line 15 with your fork's URL as well.
7. Ensure that you're in the project where your `TsscPlatform` lives, and create a `TsscPipeline` from file:
    ```bash
    oc project devsecops
    oc apply -f tssc-pipeline.yml
    ```