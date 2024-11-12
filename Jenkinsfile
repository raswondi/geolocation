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
                nexusArtifactUploader artifacts: 
                [[artifactId: "${POM_ARTIFACTID}",
                 classifier: '',
                  file: "target/${POM_ARTIFACTID}-${POM_VERSION}.${POM_PACKAGING}",
                   type: "${POM_PACKAGING}"]],
                    credentialsId: 'NexusID',
                     groupId: "${POM_GROUPID}",
                      nexusUrl: '173.255.230.111:8081',
                       nexusVersion: 'nexus3',
                        protocol: 'http',
                         repository: 'biom',
                          version: "${POM_VERSION}"

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
