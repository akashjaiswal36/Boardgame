pipeline {
    agent { label 'agent-2' }
    
    tools {
        jdk 'jdk17'
        maven 'maven3.9'
        
    }
    
    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Git branch to build')
        booleanParam(name: 'RUN_TEST', defaultValue: true, description: 'Run Test cases')
        choice(name: 'BUILD_TYPE', choices: ['debug', 'release'], description: 'Choose the build type')
    }

    stages {
        stage('Checkout Git') {
            steps {
                git branch: "${params.BRANCH_NAME}", url: 'https://github.com/akashjaiswal36/Boardgame.git'
            }
        }
        stage('Test') {
            when {
                expression {return params.RUN_TEST}
            }
            steps {
                echo "Running test......"
                sh 'mvn test'
            }
        }
        stage('Build') {
            steps {
                echo "Build type selected: ${params.BUILD_TYPE}"
                sh "mvn package -P${params.BUILD_TYPE}"
            }
        }
        stage('Env Variables lists') {
            steps {
                echo "Build ID: ${env.BUILD_ID}"
                echo "Build Number: ${env.BUILD_NUMBER}"
                echo "Job Name: ${env.JOB_NAME}"
                echo "Build URL: ${env.BUILD_URL}"
                echo "Workspace: ${env.WORKSPACE}"
                echo "Node Name: ${env.NODE_NAME}"
                
            }
        }
    }
    post {
        success {
             echo "✅ Build  is successfully completed"
        }
        failure {
            echo "❌u  Build failed please check"
        }
        always {
            echo "🎉 Done!"
        }
           
    }
}
