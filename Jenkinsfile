pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                echo "Cloning repo..."
                git url: "https://github.com/kakisatvika/CaseStudy.git", branch: 'main'
            }
        }
        stage('Build') {
            steps {
                echo "Cleaning and building the project..."
                bat "mvn clean compile"
                // 'compile' compiles the source code without running tests or packaging
            }
        }
        stage('Test') {
            steps {
                echo "Running tests..."
                bat "mvn test"
                // runs the tests without packaging
            }
        }
        stage('Deploy and Package') {
            steps {
                echo "Packaging application as JAR/WAR/EAR..."
                bat "mvn package"
             }
        }
        stage('Archive Artifacts') {
            steps {
                echo "Archive Artifacts as JAR/WAR/EAR..."
                archiveArtifacts artifacts: 'target/*.jar, target/*.war, target/*.ear'
            }
        }

    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}