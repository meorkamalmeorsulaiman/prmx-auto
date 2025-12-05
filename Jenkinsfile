pipeline {
    agent { label 'agnt-01' }

    environment {
        PROX_TOKEN_ID = "${PROX_TOKEN_ID}"
    }

    parameters {
	string(name: 'VM_ID', defaultValue: 'Enter value', description: 'Virtual machine ID')
	string(name: 'VM_NAME', defaultValue: 'Enter value',  description: 'Virtual machine name')
	string(name: 'VM_IP_ADDRESS', defaultValue: 'Enter value',  description: 'Virtual machine IP')

    }

    stages {
        stage('Creating Virutal Machine') {
            steps {
		echo "*** Creating ${params.VM_NAME} virutal machine ***"
		sh "ansible-playbook create-vm.yml -e \'api_token_secret=${env.PROX_TOKEN_ID}\'"
		echo '*** Virtual machine will start with default configuration ***'
		echo '*** Starting a 20-second wait for finishing up virtual machine... ***'
		sleep time: 20, unit: 'SECONDS'
		echo '*** Wait finished. Continuing pipeline ***'
            }
        }
        stage('Initialize Virtual Machine') {
            steps {
		echo "*** Initializing ${params.VM_NAME}. Proxmox will start ${params.VM_NAME} ***"
		sh "ansible-playbook initialize.yml -e \'api_token_secret=${env.PROX_TOKEN_ID} vm_id=${params.VM_ID} vm_name=${params.VM_NAME}\'"   
		echo '*** Starting a 20-second wait for booting up virtual machine... ***'
		sleep time: 20, unit: 'SECONDS'
		echo '*** Wait finished. Continuing pipeline ***'
	    }
        }
        stage('Reconfigure Virtual Machine') {
            steps {
		echo "*** ${params.VM_NAME} will be reconfigure as specified ***"
		sh "ansible-playbook reconfigure.yml -e \'api_token_secret=${env.PROX_TOKEN_ID} vm_id=${params.VM_NAME} vm_name=${params.VM_NAME} vm_ip_address=${params.VM_IP_ADDRESS}\'"            
		echo "*** Please restart ${params.VM_NAME} ***"
	    }
        }
    }
}
