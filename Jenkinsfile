pipeline {
    agent any
    parameters {
        choice(name: 'NAME', choices: ['faizan', 'Aman', 'Sajid'], description: 'Pick NAME')
        choice(name: 'LASTNAME', choices: ['SHAIKH', 'MOMIN', 'KHAN'], description: 'Pick LASTNAME')
        choice(name: 'SHOW', choices: ['true', 'false'], description: 'Pick something')
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Build stage executing shell script job_1.sh"'
                sh "bash job_1.sh ${params.NAME} ${params.LASTNAME} ${params.SHOW}"
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running Test Script from QA TEAM"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying on K8s Cluster"'
            }
        }
    }
    post {
        always {
            echo 'Deleting the workspace'
            deleteDir()
        }
    }
}
