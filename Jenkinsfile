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
    }
} 
