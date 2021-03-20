// Load the Ploigos Jenkins Library
library identifier: 'ploigos-jenkins-library@maven36',
retriever: modernSCM([
    $class: 'GitSCMSource',
    remote: 'https://github.com/ploigos/ploigos-jenkins-library.git'
])

// run the pipeline
ploigosWorkflowStandard(
    stepRunnerConfigDir: 'cicd/ploigos-step-runner-config/'
)
