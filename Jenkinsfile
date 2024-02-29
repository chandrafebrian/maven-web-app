pipeline {
  
    agent {
        label 'jenkins-agent'
    }
    
    tools{
        maven "Maven3Chandra"
        jdk "Java17Chandra"
    }

    stages {

        stage('Clean Workspace') {
            steps {
                CleanWs()
            }
        }

        stage('Checkout from SCM') {
            steps {
               git branch: 'main', credentialsId: 'github-chan', url: 'https://github.com/chandrafebrian/maven-web-app'
            }
        }
        stage('Build Application') {
            steps {
               sh 'mvn clean package'
            }
        }

        stage('Test Application') {
            steps {
                sh 'mvn test'
            }
        }
        
        // stage('Create Image'){
        //     steps{
        //        steps {
        //         	script {
        //         		sh 'ansible-playbook task.yml'
        //         	}
        //         }
        //     }
        // }
    }
}
