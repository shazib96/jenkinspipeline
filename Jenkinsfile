pipeline {
    agent any
    environment {
        name = "Shazib"
    }
    parameters {
        string(name: 'person', defaultValue: "Shazib Mustafa joiya", description: "Who are you?")
        booleanParam(name: 'Male', defaultValue: true, description: "")
        choice(name: 'branch', choices:  ['main', 'QA', 'dev'], description: "")
    }
    stages {
        stage('Test') {
            steps {
                sh 'ls'
                sh 'pwd'
                sh 'whoami'
                sh 'echo ${name}'
                sh 'echo "${fullname}"'
                sh 'echo "${person}"'
            }
        }
        stage('Environment Variables') {
            environment {
                fullname = "Shazib Mustafa"
            }
            steps {
                sh 'echo "$BUILD_ID"'
                sh 'echo "$JOB_NAME"'
                sh 'echo "${name}"'
                sh 'echo "${fullname}"'
            }
        }
        stage('Deploy on test') {
            input {
                message "Should we continue"
                ok "yes you can"
            }
            steps {
                echo 'Deploy to test envirnonment'
            }
        }
        stage('Deploy to prod') {
            steps {
                echo 'Deploy to the production environment'
            }
        }
        
    }
    post{
        always {
            echo "I will always execute"  
            }
        failure{
            echo "I will execute when any stage is fail or miss"
            }    
        success{
            echo "I will execute on successful job" 
        }
    }
        
}
