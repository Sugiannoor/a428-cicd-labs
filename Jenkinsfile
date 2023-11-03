    pipeline {
        agent {
            docker {
                image 'node:16-alpine' 
                args '-p 3000:3000' 
            }
        }
        stages {
            stage('Git Clone') { 
                steps {
                    git branch: 'react-app', url: 'https://github.com/sugiannoor/a428-cicd-labs'
                }
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
