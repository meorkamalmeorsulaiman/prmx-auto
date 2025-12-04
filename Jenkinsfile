pipeline {
    agent { label 'agnt-01' }
    parameters {
	string(name: 'vm_id', defaultValue: 'Enter value', description: 'Virtual machine ID')
	string(name: 'vm_name', defaultValue: 'Enter value',  description: 'Virtual machine name')
	string(name: 'vm_ip_address', defaultValue: 'Enter value',  description: 'Virtual machine IP')

    }
    stages {
        stage('Creating Virutal Machine') {
            steps {
		sh 'ansible-playbook create-vm.yml -C'
            }
        }
        stage('Initialize') {
            steps {
		echo $vm_id
            }
        }
    }
}
