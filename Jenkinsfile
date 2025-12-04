pipeline {
    agent { label 'agnt-01' }
    stages {
        stage('Creating Virutal Machine') {
            steps {
		sh 'ansible-playbook create-vm.yml -C'
            }
        }
    }
}
