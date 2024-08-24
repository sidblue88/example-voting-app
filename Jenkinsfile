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
                sh "echo hello CI JOB"
            }
            
        }
        stage('CD'){
            steps{
                sh "echo hello CD JOB"
            }
            
        }
    }
}
