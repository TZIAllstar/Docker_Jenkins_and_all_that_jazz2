def gv

pipeline{
    agent any
    environment {
        NEW_VERSION = '1.3.0'
    }
    /*tools{

        }*/
    parameters {
        choice (name: 'VERSION',choices: ['1.1.0','1.2.0'], description:'')
        booleanParam(name:'executeTests',defaultValue:true, description:'')
                
    }    
    stages {
        stage ("init"){
            script{
                gv = load "script.groovy"

            }
        }
        stage("build"){
            steps {
                gv.buildapp()
            }
        }
        stage("test"){
            /*when {
                expression {
                    env.BRANCH_NAME == 'dev' 
                }
            }*/
            when{
                expression{
                    params.executeTests == true
                }
            }            
            steps {
                echo 'testing the application..'                    
            }
        }
        stage("deploy"){
            steps {
                echo 'deploying the application..'
                echo "deploying version ${params.VERSION}"
            }
        }                
    }
}
