pipeline {
    triggers {
        pollSCM( * * * *')  // Polls every 15 minutes
    }
    agent any

    tools {
        maven 'M2_HOME'  // Ensure this is set in Jenkins Global Tool Configuration
    }

    stages {

        stage("build & SonarQube analysis") {  
            steps {
                echo 'Starting build & SonarQube analysis...'
                withSonarQubeEnv('SonarServer') { // Ensure 'SonarServer' is configured in Jenkins
                    sh 'mvn sonar:sonar'
                }
            }
        }
        
        stage('maven package') {
            steps {
                echo 'Cleaning and installing Maven project...'
                sh 'mvn clean install -DskipTests'  // Clean and install (skip tests)
                sh 'mvn package -DskipTests'        // Package the application (skip tests)
            }
        }
        
        stage('test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'  // Run tests after packaging
            }
        }
    }
}
