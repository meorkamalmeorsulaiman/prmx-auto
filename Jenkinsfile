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
    		// Will print the masked value of the KEY, replaced with ****
		maskPasswords(varPasswordPairs: [[var: '${env.PROX_TOKEN_ID}']], varMaskRegexes: []) {
			echo "Masked password parameter ${env.PROX_TOKEN_ID}"
		}
            }
        }
    }
}
