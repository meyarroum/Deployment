pipeline {

    agent any


    stages {
       stage ('Pull') {
            steps {
               script{
						checkout([$class: 'GitSCM',
     branches: [[name: "*/master" ]],
     userRemoteConfigs: [[credentialsId: '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', url: 'https://github.com/meyarroum/Deployment.git']]
         ])
				    }
            }
        }
		
		/*stage ('Build') {
            steps {
               script{
						sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml "
				    }
            }
        }*/
		
		stage ('docker') {
            steps {
               script{
						sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml "
				    }
            }
        }

stage('dockerHub') {
             steps{
                script{
                    sh "ansible-playbook ansible/register.yml -i Ansible/inventory/host.yml"
                }
            }
        }

    }   
}
