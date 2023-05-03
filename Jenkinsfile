pipeline {
      agent any
      stages {
            stage ('Build') {
                  steps {
                        sh 'mvn -f java-tomcat-sample/pom.xml clean package'
                  }
            }
            stage ('Archive artifacts') {
                  steps {
                        archiveArtifacts artifacts: '**/*.war'
                  }
            }
            stage ('Deploy to Production') {
                  steps {
                        build job: 'Deploy_application'
                  }
            }
      }
}