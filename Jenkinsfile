pipeline
{
   agent any
   
    stages {
        
     stage('Pull') {
         
     steps{
       script{
     checkout([$class: 'GitSCM', branches: [[name: '*/main']],
         userRemoteConfigs: [[
         
         url:'https://github.com/waellb/projetCD.git']]])
         
         }
         
         }
         
         }
         
         stage('build')
         {
             steps{
                 script{
                     sh "ansible-playbook Ansible/build.yml -i Ansible/inventory/host.yml -e ansible_become_password=wael53955994"
                 }
             }
         }
         
         stage('docker'){
            steps{
                script{
                    sh "ansible-playbook Ansible/docker.yml -i Ansible/inventory/host.yml -e ansible_become_password=wael53955994"
                }
            }
        }
        
         stage('docker-registry'){
            steps{
                script{
                    sh "ansible-playbook Ansible/docker-registry.yml -i Ansible/inventory/host.yml -e ansible_become_password=wael53955994"
                }
            }
        }
        
         
         }
         
         
}
