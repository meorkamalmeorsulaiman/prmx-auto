pipeline {
    agent { label 'agnt-01' }
    parameters {
	string(name: 'VM_ID', defaultValue: 'Enter value', description: 'Virtual machine ID')
	string(name: 'VM_NAME', defaultValue: 'Enter value',  description: 'Virtual machine name')
	string(name: 'VM_IP_ADDRESS', defaultValue: 'Enter value',  description: 'Virtual machine IP')

    }
    stages {
        stage('Creating Virutal Machine') {
            steps {
		sh 'ansible-playbook create-vm.yml -C'
            }
        }
        stage('Initialize') {
            steps {
		echo "${params.VM_ID}"
            }
        }
    }
}
