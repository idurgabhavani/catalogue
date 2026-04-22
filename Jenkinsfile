pipeline{
    agent any
    // {
    //     node{
    //         label 'AGENT-1'
    //     }
    // }

    environment {
        packageVersion = '' // our package version changes every time so we need to check the package version
    } // if we placed this variable in environment means we can use this in all the stages

    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }

    stages {
        stage('Get the version') {
            steps{
                script {  // if it is shell command we can give sh but this we are using grrovy scripting
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.version
                    echo "application version: $packageVersion"

                


                }
            }


        }
        stage('Install dependies') {
            steps {
                sh """
                npm install

                """
                
            }

        }
        stage('Build') {
            steps {
                sh """

                ls -la
                zip -r catalogue.zip ./* -x ".git" -x "*.zip"
                ls -ltr

                """
            }
        }
    }

    post {
        always {
            echo 'i will say hello again'
            echo 'here we are deleting the directories after runnigng the pipeline'
            deleteDir()
            cleanWs()
        }
    }
}

