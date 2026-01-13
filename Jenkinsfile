pipeline{
    // agent { label 'AGENT-1' }
    agent any
    environment {
        PROJECT = 'EXPENSE'
        COMPONENT = 'BACKEND' 
        DEPLOY_TO = "production"

    }
    options {
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'person', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'bio', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'toggle', defaultValue: true, description: 'Toggle this value')

        choice(name: 'choice', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'password', defaultValue: 'SECRET', description: 'Enter a password')
    }
    stages{
        stage("first"){
            steps{
                echo " this is my first step"
            }
            }
        stage("second"){
            steps{
                echo " $PROJECT AND $COMPONENT "
            }
        }
        stage("parameters"){
            steps{
                echo "person  $params.person"
                echo "bio $params.bio"
                echo "ToGGLE $params.toggle"
                echo "passwoed $params.password"
            }
        }
        stage('Parallel Stage') {
            when {
                expression { params.toggle == true }
            }
            parallel {
                stage('Branch A') {
                    steps {
                        echo "On Branch A"
                    }
                }
                stage('Branch B') {
                    steps {
                        echo "On Branch B"
                    }
                }
                stage('Branch C') {
                          steps {
                                echo "In stage Nested 1 within Branch C"
                            }
                        }
                       
                    }
                }
            }
    post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()
        }
        failure { 
            echo 'I will run when pipeline is failed'
        }
        success { 
            echo 'I will run when pipeline is success'
        }
    }
}
    