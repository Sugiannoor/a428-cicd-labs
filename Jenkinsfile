node {
    def customImage = docker.image('node:16-alpine')
    
    try {
        customImage.run("-p 3000:3000") {
            stage('Git Clone') {
                checkout([$class: 'GitSCM', branches: [[name: 'react-app']], userRemoteConfigs: [[url: 'https://github.com/sugiannoor/a428-cicd-labs']]])
            }
            
            stage('Build') {
                sh 'npm install'
            }
            
            stage('Test') {
                sh './jenkins/scripts/test.sh'
            }
        }
    } finally {
        customImage.stop()
    }
}
