pipeline {
    agent {
        label 'AGENT-1'
    }
     options{
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds() // No Multiple  Builds
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
      environment{
        DEPLOY_TO = 'production'
        GREETING =  'Good Morning'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo This is Build'
            }
        }
        stage('Test') {
            steps {
                sh 'echo This is Test'
                sh 'sleep 10'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo This is Deploy'
            }
        }
        stage("print params"){
            steps{
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
                echo "Trigger Test"
                errror "Some Failure"
            }
        }
    }
    post{ //This will catch the event and send Alerts to Mail/Slack
        always{
            echo 'Always say hello Again'
        }
        success{
            echo 'I will run when pipelin is SUCCESS'
        }
        failure{
            echo 'I will run when pipeline is Failure'
        }
    }
}