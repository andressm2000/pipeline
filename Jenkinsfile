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
                sh "mvn clean package -DskipTests=true -f complete/pom.xml"
            }
        }
		stage('Test') {
            steps {
                // Get some code from a GitHub repository
                // git 'https://github.com/andressm2000/pipeline.git'

                // Run Maven on a Unix agent.
                sh "mvn test -f complete/pom.xml"
            }
        }
		stage('Deploy') {
            steps {
                // Get some code from a GitHub repository
                // git 'https://github.com/andressm2000/pipeline.git'

                // Run Maven on a Unix agent.
                sh "mvn spring-boot:run -f complete/pom.xml"
            }
        }
    }
}
