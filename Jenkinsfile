node {
    stage('SCM Checkout') {
        git 'https://github.com/l-pizarro/frontend'
    }
    stage('Compile ') {
        sh 'npm run build'
    }
}