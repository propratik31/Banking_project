pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/propratik31/Banking_project'
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
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }
         stage('Config & Deployment') {
            steps {
                    sh 'sudo chmod 600 myjenkins.pem'
                    sh 'terraform init'
                    sh 'terraform validate'
                    sh 'terraform apply --auto-approve'
}
    }
}
}
    }
}
