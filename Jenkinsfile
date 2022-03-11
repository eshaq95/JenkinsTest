pipeline {
    agent any
  stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') { 
            steps {
                bat 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
           stage('Deliver for development') {
            when {
                branch 'development' 
            }
            steps {
               echo 'Delivering for development from development branch'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'master'  
            }
            steps {
                echo 'Deploying working software from master branch code'
            }
          }
        }
    }

