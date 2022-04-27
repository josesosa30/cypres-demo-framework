pipeline
{

    /*Pipeline Declarativo*/
    
    agent any
    
    parameters {
        string(name: "SPEC", defaultValue: "cypress/integration/pom/*.spec.js",description: "RunFile SpecTest")
        choice(name: "BROWSER", choices: ['chrome','edge'],description: "Seleccionar un browser para trabajar")
            
    }
    
    option {
     ansicolor('xterm')
    }
    
    stages{
        stage('Build'){
             steps{
                echo "Building Application"
             }
        }
        stage('Testing'){
             steps{
                bat "nmp i"
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
        always{
            publishHTML([allowMissing:false, alwaysLinkToLastBuild:false, keepAll: true, reportDir: 'cypress/report', reportFiles: 'index.html', reportName:'HTML Report', reportTitles:''])
        }
    }
}