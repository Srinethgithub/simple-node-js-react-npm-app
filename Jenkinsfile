pipeline {
    agent any  // any agent, or docker { image 'node:20' } for better isolation

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Srinethgithub/simple-node-js-react-npm-app.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'  // creates build/ folder
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'  // if tests unnayi, run avuthayi
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build/**', fingerprint: true, allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed!'
        }
    }
