pipeline {
    agent any
    options {
        buildDiscarder(logRotator(artifactNumToKeepStr: '5'))
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -Drevision=1.0.3 clean install'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'BeyondPaper-Server/target/paper-*.jar', followSymlinks: false
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn -Drevision=1.0.3 deploy -DskipTests'
            }
        }
    }
}
