pipeline{
    agent any
    environment{
        DIRECTORY_PATH="C:/Users/CYN/Deakin Uni/SIT753-Professional Practice in IT/Task 8.1C"
        TESTING_ENVIRONMENT="cyn-test-environment"
        PRODUCTION_ENVIRONMENT="CynthiaWijaya"
    }
    stages{
        stage('Build'){
            steps{
                echo "Fetch the source code from the directory path specified by the environment variable: ${env.DIRECTORY_PATH}"
                echo "Build the code using npm and webpack"
            }
        }
        stage('Unit and Integration Test'){
            steps{
                script{
                    echo "Run unit test using Mocha and Chai to ensure the code functions as expected"
                    echo "Run integration test using Jest to ensure the components in web app work together as expected"
                    sh 'echo Running Jest and test...' 
                }
                
            }
            post{
                    always{
                            emailext (
                                to: 'prettybluesky135@gmail.com',
                                subject: "Unit and Integration Test - ${currentBuild.currentResult}",
                                body: "The Unit and Integration Test stage finished with status: ${currentBuild.currentResult}. See attached log.",
                                attachLog: true
                            )
                    }
            }
        }
        stage('Code Analysis'){
            steps{
                echo "Analyse the quality of the code using SonarQube"
            }
        }
        stage('Security Scan'){
            steps{
                echo "Perform a security scan on the code using npm audit to identify vulnerabilities in npm dependencies"
                sh 'echo Running npm audit...' 
            }
            post{
                    always{
                            emailext (
                                to: 'prettybluesky135@gmail.com',
                                subject: "Unit and Integration Test - ${currentBuild.currentResult}",
                                body: "The Unit and Integration Test stage finished with status: ${currentBuild.currentResult}. See attached log.",
                                attachLog: true
                            )
                    }
            }
            post {
                always {
                        emailext (
                                to: 'prettybluesky135@gmail.com',
                                subject: "Security Scan - ${currentBuild.currentResult}",
                                body: "The Security Scan stage finished with status: ${currentBuild.currentResult}. See attached log.",
                                attachLog: true
                        )
                }
            }
        }
        stage('Integration Test on Staging'){
            steps{
                echo "Deploy the web application to a staging server AWS EC2 instance"
            }
        }
        stage('Deploy to Production'){
            steps{
                echo "The code is being deployed to the production server AWS EC2 instance"
            }
        }
        stage('Complete'){
            steps{
                echo "All stages were successfully completed"
            }
        }
    }
}


/*pipeline{
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/cynthiawjy135/8.2CDevSecOps.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        // stage('Run Tests') {
        //     steps {
        //         script {
        //             def testStatus = 'SUCCESS'
        //             try {
        //                 echo 'Doing test using Mocha and Chai'
        //                 //sh 'npm test | tee test.log'
        //             } catch (e) {
        //                 testStatus = 'FAILURE'
        //             }

                    /*sh 'ls -lh test.log'

                    archiveArtifacts artifacts: 'test.log', onlyIfSuccessful: false*/

                    /*emailext (
                        to: "prettybluesky135@gmail.com",
                        subject: "Test Stage: ${testStatus}",
                        body: "The testing stage finished with status: ${testStatus}. See attached test log.",
                        attachLog: true
                        //attachmentsPattern: 'test.log',
                        //recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']]
                    )*

                    /*def testLog = readFile('test.log')

                    mail to: "prettybluesky135@gmail.com",
                         subject: "Test Stage: ${testStatus}",
                        body: """The test stage finished with status: ${testStatus}.

===== Test Log =====

${testLog}
"""*/
            //     }
            // }post {
            //     always {
            //         emailext(
            //             subject: "Jenkins Job - Integration Tests on Staging: ${currentBuild.result}",
            //             body: "The 'Integration Tests on Staging' stage has completed with status: ${currentBuild.result}",
            //             to: "prettybluesky135@gmail.com",
            //             attachLog: true
            //         )
            //     }
            // }

        //}
        /*
        stage('Run Tests') {
            steps {
                script {
                    def testStatus = 'SUCCESS'
                    try {
                        echo 'Doing test using Mocha and Chai'
                        //sh 'npm test | tee test.log'
                    } catch (e) {
                        testStatus = 'FAILURE'
                    }

                }
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins Job - Integration Tests on Staging: ${currentBuild.result}",
                        body: "The 'Integration Tests on Staging' stage has completed with status: ${currentBuild.result}",
                        to: "prettybluesky135@gmail.com",
                        attachLog: true
                    )
                }
            }
        }
        stage('Generate Coverage Report') {
            steps {
                // Ensure coverage report exists
                sh 'npm run coverage || true'
            }
        }
        stage('NPM Audit (Security Scan)') {
            steps {
                script {
                    def auditStatus = 'SUCCESS'
                    try {
                        sh 'npm audit | tee audit.log'
                    } catch (e) {
                        auditStatus = 'FAILURE'
                    }
                    /*emailext (
                        to: "prettybluesky135@gmail.com",
                        subject: "Security Scan Stage: ${auditStatus}",
                        body: """The security scan stage was completed with status: ${auditStatus}.""",
                        attachmentsPattern: 'audit.log',
                        recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']]
                    )*/
/*
                    def auditLog = readFile('audit.log')

                    mail to: "prettybluesky@gmail.com",
                        subject: "Security Scan Stage: ${auditStatus}",
                        body: """The security scan stage finished with status: ${auditStatus}.

===== Audit Log =====

${auditLog}
"""
                }
            }
        }
    }
}
*/