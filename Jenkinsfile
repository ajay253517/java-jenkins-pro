pipeline {
    agent {
      label "master"
    }
    stages {
      stage('checkout') {
        steps {
              checkout([
                $class: 'GitSCM', 
                branches: [[name: '*/main']], 
                extensions: [], 
                userRemoteConfigs: 
                    [[credentialsId: 'jenkins-master-github-key', 
                      url: 'git@github.com:ajay253517/java-jenkins-pro.git']]])
           }
        }             
         stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
    }
}