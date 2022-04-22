pipeline{
    agent  any
    
    tools{
        maven 'maven3'
        jdk 'JDK'
    }
    stages{
        stage("Build Maven"){
            steps{
                echo "========executing Build Maven========"
                sh 'pwd'
                sh 'mvn clean install '
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("Copy artifact"){
            steps{
                echo "========executing Build Maven========"
                sh 'pwd'
                
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
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