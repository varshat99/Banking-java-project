pipeline{
    agent any
    environment {
        DOCKER_BUILDKIT = '1'
        DOCKER_CLI_PLUGIN_PATH = '/usr/libexec/docker/cli-plugin'
    }
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/varshat99/Banking-java-project.git'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with akshat'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with akshat'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with akshat'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with akshat'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker buildx version'
               sh 'docker buildx build -t my-img:latest .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
