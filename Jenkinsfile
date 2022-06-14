pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/santosh-erra/santosh-devops']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t santosherra/devops-integration .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   
                   sh 'docker login -u santosherra -p Santosh@2'

                   sh 'docker push santosherra/devops-integration'
                }
            }
        }
    }
}