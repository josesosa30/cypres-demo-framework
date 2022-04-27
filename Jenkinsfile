pipeline
{

    /*Pipeline Declarativo*/
    
    agent any
    
    parameters {
        string(name: "SPEC", defaultValue: "cypress/integration/pom/*.spec.js",description: "RunFile SpecTest")
        choice(name: "BROWSER", choices: ['chrome','edge'],description: "Seleccionar un browser para trabajar")
            
    }
    
    /*options {
     ansiColor('xterm')
    }*/
    
    stages{
        stage('Build'){
             steps{
                echo "Building Application"
             }
        }
        stage('Testing'){
             steps{
                bat "npm i"
                bat "npx cypress run --browser ${BROWSER} --spec ${SPEC}"
             }
        }
        
        stage('Deploy'){
             steps{
                echo "Deploying Application"
             }
        }
    }
    
    post{
        success{mail to: 'jose.sosa090530@gmail.com', subject: 'The Pipeline success'}
    }
}