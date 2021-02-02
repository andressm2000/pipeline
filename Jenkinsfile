pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "MAVEN_HOME"
    }

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/andressm2000/pipeline.git'

                // Run Maven on a Unix agent.
                sh "mvn clean package -DskipTest=true -f complete/pom.xml"
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
		stage('Test') {
            steps {
                // Get some code from a GitHub repository
                // git 'https://github.com/andressm2000/pipeline.git'

                // Run Maven on a Unix agent.
                sh "mvn test -f complete/pom.xml"
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
                // Get some code from a GitHub repository
                // git 'https://github.com/andressm2000/pipeline.git'

                // Run Maven on a Unix agent.
                sh "mvn spring-boot:run -f complete/pom.xml"
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
    }
}