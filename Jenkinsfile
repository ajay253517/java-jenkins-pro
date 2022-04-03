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
         stage('Deploy Ansible'){
           steps {
             sh "ansible-playbook main.yml -i inventories/dev/hosts --user admin-user --key-file /var/lib/jenkins/.ssh/id_rsa"
           }
         }
    }
}