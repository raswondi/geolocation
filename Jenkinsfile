pipeline {
   agent any
   tools {
    maven 'M2_HOME'
}
stages{
    stage('maven build'){
        steps{
            sh mv clean install package
            }
        }
    }
} 
