pipeline {
   agent any
   tools {
    maven 'M2_HOME'
}
stages{
    stage('maven build'){
            steps{
                sh 'mvn clean install package -DargLine="--add-opens java.base/java.lang=ALL-UNNAMED"'


            }
        }
        stage('check pwd'){
            steps{
                sh 'pwd'


            }
        }
        stage('list directory'){
            steps{
                sh 'ls'


            }
        }
        stage('check direcotry'){
            steps{
                sh 'whoami'


            }
        }
    }
} 
