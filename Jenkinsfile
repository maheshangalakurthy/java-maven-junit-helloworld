pipeline{
    agent{
        label "master"
    }
    options{
        timestamps()
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    triggers{
        pollSCM('* * * * *')
    }
    tools {
        maven 'maven3'
       // jdk 'jdk8'
    }
    stages{
        stage("Git Checkout"){
            steps{
                echo "========executing Git Checkout========"
                git branch: 'master', credentialsId: 'github', url: 'https://github.com/maheshangalakurthy/java-maven-junit-helloworld.git'
            }
            post{
                always{
                    echo "========successfully Cloned========"
                }
                success{
                    echo "========successfully Cloned========"
                }
                failure{
                    echo "========Checkout is failed========"
                }
            }
        }

        stage('Maven Build'){
            steps{
            echo "=========== Maven Build =============="
            //tool name: 'maven3', type: 'maven'
            sh "mvn package"
            
            }
            post{
                always{
                    echo "========Maven Build Done========"
                   // cleanWs()
                }
                success{
                    echo "========Maven Build Done========"
                }
                failure{
                    echo "========Maven Build failed========"
                }
            }

        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}