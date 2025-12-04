pipeline {
    agent { label 'agnt-01' }
    parameters {
	string(name: 'vm_id', description: 'Virtual machine ID')
	string(name: 'vm_name', description: 'Virtual machine name')
	string(name: 'vm_ip_address', description: 'Virtual machine IP')

    }
    stages {
        stage('Creating Virutal Machine') {
            steps {
		sh 'ansible-playbook create-vm.yml -C'
            }
        }
    }
}
