pipeline {
    agent any
    stages {
        stage ('Checkout') {
            steps {
                git branch:'master', url: 'https://github.com/nlct2k/Vulnerable-Web-Application.git'
            }
        }

        stage('Code Quality Check via SonarQube') {
            steps {
                script {
                def scannerHome = tool 'SonarQube';
                    withSonarQubeEnv('SonarQube') {
                    sh "/var/jenkins_home/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarQube/bin/sonar-scanner -Dsonar.projectKey=OWASP -Dsonar.sources=.}
                }
            }
        }
    }
    post {
        always {
            recordIssues enabledForFailure: true, tool: sonarQube()
        }
    }
}

