pipeline {
    agent any

        stages {
        stage("checkout") {
            steps {
                sh "https://github.com/Jagga-1309/hello-world-war.git"
            }
        }
        stage("build") {
            steps {
                sh "mvn package"
            }
        }
        stage('Push artifacts into artifactory') { 
            steps { 
              rtUpload ( 
                serverId: 'myartifactory', 
                    spec: '''{ 
                      "files": [ 
                          { 
                            "pattern": "*.war", 
                            "target": "example-repo-local/" 
                           } 
                         ] 
                       }''' 
                      ) 
                 } 
              }
}
}