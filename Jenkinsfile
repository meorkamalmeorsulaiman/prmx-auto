pipeline {
    agent { label 'agnt-01' }

    environment {
        PROX_TOKEN_ID = "${PROX_TOKEN_ID}"
    }

    parameters {
		string(name: 'VM_ID', defaultValue: 'Virtual machine ID', description: 'Virtual machine ID')
		string(name: 'VM_NAME', defaultValue: 'Virtual machine name',  description: 'Virtual machine name')
		string(name: 'VM_IP_ADDRESS', defaultValue: 'IP address',  description: 'Virtual machine IP')

    }

    stages {
        stage('Creating Virtual Machine') {
            steps {
				echo "*** Creating ${params.VM_NAME} virtual machine ***"
				maskPasswords(varPasswordPairs: [[var: '${env.PROX_TOKEN_ID}']], varMaskRegexes: []) {
					sh "ansible-playbook playbook/create-vm.yml -e \'api_token_secret=${env.PROX_TOKEN_ID}\'"
				}
				echo '*** Virtual machine will start with default configuration ***'
				echo '*** Starting a 20-second wait for finishing up virtual machine... ***'
				sleep time: 20, unit: 'SECONDS'
				echo '*** Wait finished. Continuing pipeline ***'
            }
        }
    }
}
