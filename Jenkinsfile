pipeline {
      agent any
      stages {
            stage ('Build') {
                  steps {
                        sh 'mvn -f java-tomcat-sample clean package'
                  }
            }
            stage ('Archive artifacts') {
                  steps {
                        archiveArtifacts artifacts: '**/*.war'
                  }
            }
            stage ('Deploy to Staging') {
                  steps {
                        build job: 'Deploy_application'
                  }
            }
            stage ('Deploy to Production') {
                  steps {
                        timeout(time:5, unit:'DAYS'){
                              input message: 'Approve Production Deployment?'
                        }
                        build job: 'Deploy_application_to_prod'
                  }
            }
      }
}