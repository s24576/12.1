pipeline {
    agent any
    
    triggers {
        gitlab(triggerOnPush: true, triggerOnMergeRequest: true, branchFilterType: 'All', includeBranches: '*')
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/s24576/12.1.git'
            }
        }
        stage('Test') {
            steps {
                sh 'python3 -m unittest discover'
            }
        }
    }
    
    post {
        always {
            junit 'test-reports/*.xml'
        }
        success {
            echo 'Tests passed successfully!'
        }
        failure {
            echo 'Tests failed. Please check the output for details.'
        }
    }
}
