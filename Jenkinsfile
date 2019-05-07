pipeline {
    agent any tools {
        nodejs "node"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/l-pizarro/frontend'
            }
        }
    }
}