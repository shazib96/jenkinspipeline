pipeline {
    agent any
    environment {
        name = "Shazib"
    }
     parameters {
        string(name: 'DEPLOY_ENV', defaultValue: 'staging', description: '')
        text(name: 'DEPLOY_TEXT', defaultValue: 'One\nTwo\nThree\n', description: '')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
         choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
         file(name: 'FILE', description: 'Some file to upload')
         password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'A secret password')
    }
    parameters {
        string(name: 'person', defaultValue: "Shazib Mustafa joiya", description: "Who are you?")
        booleanParam(name: 'Male', defaultValue: true, description: "")
        choice(name: 'branch', choices:  ['main', 'QA', 'dev'], description: "")
    }
    stages {
        stage('string'){

         steps{
         echo " string $DEPLOY_ENV"
         }
         }
        stage('text'){

         steps{
         echo " text $DEPLOY_TEXT"
         }
         }
        stage('booleanParam'){

         steps{
         script{
         if(TOGGLE){
         echo " now execute, booleann is true"
        }else{
         echo " Dont execute, boolean is true"
        }
         }
        }
         }
        stage('choice'){

         steps{
        script{
        if(DEPLOY_ENV=='staging'){
        echo " choice $CHOICE"
        }
         }
        }
         }
        stage('file'){

         steps{
         echo " file $FILE"
         }
         }
        stage('password'){

         steps{
         echo " password $PASSWORD"
         }
         }
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
