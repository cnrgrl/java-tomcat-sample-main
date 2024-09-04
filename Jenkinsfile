pipeline {
    agent any
    stages {
        stage('Build Application') {
             steps{
                build job: 'build-web-application'
            }
        }
        stage('Deploy to Staging Environment'){
            steps{
                build job: 'Deploy-Application-Staging-Environment'
            }            
        }
        stage('Deploy to Production Environment'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    script {
                def userInput = input(
                    message: 'PRODUCTION Dağıtımını Onayla?',
                    ok: 'Evet',
                    parameters: [booleanParam(defaultValue: false, description: '', name: 'İptal')]
                )
                }
                build job: 'Deploy-Application-Production-Environment'
            }
        }
    }
}
}
