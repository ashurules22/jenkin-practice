pipeline {
    agent any
    environment {
        name = 'Ashutosh'
    }
    
    parameters {
        string(name: 'person', defaultValue: 'nishant', description: '')
        booleanParam(name: 'DEBUG_BUILD', defaultValue: true, description: '')
        choice(name: 'CHOICES', choices: ['one', 'two', 'three'], description: '')
    }

    stages {
        stage('run as command') {
            steps {
                sh 'date'
            }
        }
        
        stage('run many command at once') {
            steps {
                sh '''
                date
                ls
                pwd
                cal 2021
                '''
            }
        }
        
        stage('print environment variable') {
            environment {
                username = 'usernameislocal'
             }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
            }
        }
        
        
        stage('continue ?') {
            
            input {
                message "should we continue?"
                ok "yes we should continue"
            }
            steps {
                echo 'deply in production'
               
            }
       
        }
             
            
        stage('deploy-in-prod') {
            steps {
                echo 'this is deployment in prod'
                sh 'echo "${username}"'
                sh 'echo "${person}"'
                sh 'echo "${DEBUG_BUILD}"'
                sh 'echo "${CHOICES}"'
            }
       
        }
    }
    
    post{
        
        always{
            echo "i will always say hello again"
        }
        
        failure{
            echo "some build failed"
        }
        
        success{
            echo "all builds are successfully executed"
        }
        
    }
    
}
