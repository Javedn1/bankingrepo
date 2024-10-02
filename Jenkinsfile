pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/Javedn1/bankingrepo'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with nabeel'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with nabeel'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with nabeel'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with nabeel'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
