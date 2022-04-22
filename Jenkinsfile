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
                sh 'mvn clean install'
            //    sh  'chmod 700 mvnw && ./mvnw clean install package'
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
                echo "========executing Copy artifact========"
                sh 'pwd'
                sh 'cp -r target/*.jar docker'
                
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
        stage("Build Docker Image"){
            steps{
                echo "========executing Build Docker Image========"
                sh 'pwd'
                script{
                    def CustomImage = docker.build('soamibm/petclinic','./docker')
                    docker.withRegistry('https://hub.docker.com','dockerhub_cred')
                    CustomImage.push("${env.BUILD_NUMBER}")
                }
                
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