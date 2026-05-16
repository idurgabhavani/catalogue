pipeline{
    agent {
        node {
            label 'agent-1'
        }
    }
    environment {
        packageVersion = ''
        nexusURL = ''
    }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }
    
}