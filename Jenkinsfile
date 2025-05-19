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
                echo "Run unit test using Mocha and Chai to ensure the code functions as expected"
                echo "Run integration test using Jest to ensure the components in web app work together as expected"
            }
            post{
                    always{
                        mail to: "prettybluesky@gmail.com",
                        subject: "Testing Status Notification",
                        body: "Unit Test and Integration Test was successful"
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
