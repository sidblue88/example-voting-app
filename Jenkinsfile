pipeline{
    agent {label 'worker'}
    options{
        buildDiscarder(logRotator(numToKeepStr: '5'))
        disableConcurrentBuilds()
        retry(2)
        timeout(time: 10, unit: 'MINUTES')
    }
    triggers { cron('H */4 * * 1-5') }
    stages{
        stage('CI'){
            steps{
                sh '''
                cd vote
                aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 584716546011.dkr.ecr.us-east-1.amazonaws.com
                docker build -t 584716546011.dkr.ecr.us-east-1.amazonaws.com/demo-c49:v${BUILD_NUMBER} .
                '''
            }
            
        }
        stage('CD'){
            steps{
                sh "echo hello CD JOB"
            }
            
        }
    }
}
