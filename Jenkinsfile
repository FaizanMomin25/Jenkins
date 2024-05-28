pipeline {
    agent any
    environment {
        my_account = "${params.ACCOUNT_NAME}"
    }
    parameters {
        choice(name: 'ACCOUNT_NAME', choices: ['DEV', 'QA'], description: 'Picks AWS Account')
    }
    stages {
        stage('Deploy in DEV') {
            when {
                expression {
                    params.ACCOUNT_NAME == 'DEV'
                }
            }
            steps {
                sh "echo Building the project in DEV account."
                script {
                    getAccountNumber(env.my_account)
                }
            }
        }
        stage('Deploy in QA') {
            when {
                expression {
                    params.ACCOUNT_NAME == 'QA'
                }
            }
            steps {
                sh "echo Building the project in QA account."
                script {
                    getAccountNumber(env.my_account)
                }
            }
        }
    }
    post {
        always {
            echo 'Deleting Workspace'
            deleteDir()
        }
    }
}

def getAccountNumber(String Acc_name) {
    if (Acc_name == 'DEV') {
        sh "echo Hello from getAccountNumber function, DEV AWS Account ID: 187547857487"
    } else if (Acc_name == 'QA') {
        sh "echo Hello from getAccountNumber function, QA AWS Account ID: 187547857498"
    } else {
        sh "echo Invalid Account Name: ${Acc_name}"
    }
}
