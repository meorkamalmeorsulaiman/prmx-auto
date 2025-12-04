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
		echo "*** Creating ${params.VM_NAME} virutal machine ***"
		sh 'ansible-playbook create-vm.yml'
		echo '*** Virtual machine will start with default configuration ***'
            }
        }
        stage('Initialize Virtual Machine') {
            steps {
		echo "*** Initializing ${params.VM_NAME}. Proxmox will start ${params.VM_NAME} ***"
		sh "ansible-playbook initialize.yml -e \'vm_id=${params.VM_ID} vm_name=${params.VM_NAME}\'"            
	    }
        }
        stage('Reconfigure Virtual Machine') {
            steps {
		echo "*** ${params.VM_NAME} will be reconfigure as specified ***"
		sh "ansible-playbook reconfigure.yml -e \'vm_id=${params.VM_NAME} vm_name=${params.VM_IP_ADDRESS}\'"            
		echo "*** Please restart ${params.VM_NAME} ***"
	    }
        }
    }
}
