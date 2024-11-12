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
        stage('upload'){
            steps{
                sh 'pwd'


            }
        }
        stage('upload artifact'){
            steps{
                script{
                def mavenPom = readMavenPom file: 'pom.xml'
                nexusArtifactUploader artifacts: 
                [[artifactId: "${mavenPom.artifactId}",
                 classifier: '',
                  file: "target/${mavenPom.artifactId}-${mavenPom.version}.${mavenPom.packaging}",
                   type: "${mavenPom.packaging}"]],
                    credentialsId: 'NexusID',
                     groupId: "${mavenPom.groupId}",
                      nexusUrl: '173.255.230.111:8081',
                       nexusVersion: 'nexus3',
                        protocol: 'http',
                         repository: 'biom',
                          version: "${mavenPom.version}"

                }
            }
        }
        stage('check direcotry'){
            steps{
                sh 'whoami'


            }
        }
    }
} 
