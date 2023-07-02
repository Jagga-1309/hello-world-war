pipeline {
    agent any

        stages {
        stage("checkout") {
            steps {
                sh "git clone https://github.com/Jagga-1309/hello-world-war.git"
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
        stage ('copy') {
            steps {
                sh 'scp /var/lib/jenkins/workspace/demo_pipeline_jfrog/target/hello-world-war-1.0.1.war /opt/apache-tomcat-8.5.5.90/webapps/'
            }
        }
}
}
