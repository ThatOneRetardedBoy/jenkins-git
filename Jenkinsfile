pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'mvn clean install' 
            }
        }
        stage('Post Build') { 
            steps {
                archiveArtifacts artifacts: '*/*war', followSymlinks: false
            }
        }
        stage('Deploy') { 
            steps {
                deploy adapters: [tomcat9(credentialsId: 'deployer-spark', path: '', url: 'http://localhost:8080')], contextPath: 'spark/', war: 'target/sparkjava-hello-world-1.0.war' 
            }
        }
    }
}
