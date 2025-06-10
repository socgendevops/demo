pipeline {
    agent any

    tools {
        // Install the Maven version configured as "maven-3.9.10" and add it to the path.
        maven "maven-3.9.10"
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', url: 'https://github.com/gscprojectdemo/maven-spring.git'
                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
         stage('Deploy') {
            steps {
                echo "deployment step here"
            }
        }
        stage('test') {
            steps {
                echo "test execution step here"
            }
        }
    }
}
