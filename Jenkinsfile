// Load the Ploigos Jenkins Library
library identifier: 'ploigos-jenkins-library@main',
retriever: modernSCM([
    $class: 'GitSCMSource',
    remote: 'https://github.com/ploigos/ploigos-jenkins-library.git'
])

// run the pipeline
ploigosWorkflowStandard(
    stepRunnerConfigDir: 'cicd/ploigos-step-runner-config/',
    pgpKeysSecretName: 'tssc-gpg-key',

    workflowServiceAccountName: 'jenkins',

    workflowWorkerImageDefault: 'quay.io/ploigos/ploigos-ci-agent-jenkins:v0.16.0',
    workflowWorkerImageUnitTest: 'quay.io/akrohg/ploigos-tool-maven36:latest',
    workflowWorkerImagePackage: 'quay.io/akrohg/ploigos-tool-maven36:latest',
    workflowWorkerImageStaticCodeAnalysis: 'quay.io/ploigos/ploigos-tool-sonar:v0.16.0',
    workflowWorkerImagePushArtifacts: 'quay.io/akrohg/ploigos-tool-maven36:latest',
    workflowWorkerImageContainerOperations: 'quay.io/ploigos/ploigos-tool-containers:v0.16.0',
    workflowWorkerImageContainerImageStaticComplianceScan: 'quay.io/ploigos/ploigos-tool-openscap:v0.16.0',
    workflowWorkerImageContainerImageStaticVulnerabilityScan: 'quay.io/ploigos/ploigos-tool-openscap:v0.16.0',
    workflowWorkerImageDeploy: 'quay.io/ploigos/ploigos-tool-argocd:v0.16.0',
    workflowWorkerImageValidateEnvironmentConfiguration: 'quay.io/ploigos/ploigos-tool-config-lint:v0.16.0',
    workflowWorkerImageUAT: 'quay.io/akrohg/ploigos-tool-maven36:latest',

    separatePlatformConfig: true,
    stepRunnerLibSourceUrl: "git+https://github.com/ploigos/ploigos-step-runner.git@main",
    stepRunnerUpdateLibrary: true,
    workflowWorkersImagePullPolicy: 'Always'
)
