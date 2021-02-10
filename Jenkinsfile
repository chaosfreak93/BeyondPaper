pipeline {
    agent any
    options {
        buildDiscarder(logRotator(artifactNumToKeepStr: '5'))
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'BeyondPaper-Server/target/paper-*.jar', followSymlinks: false
                }
            }
        }
    }
}
