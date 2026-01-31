pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo "----------- build started ----------"
                sh 'mvn -v'
                sh 'mvn clean package -DskipTests'
                echo "----------- build completed ----------"
            }
        }

        stage("Test") {
            steps {
                echo "----------- unit test started ----------"
                sh 'mvn test'
                sh 'mvn surefire-report:report || true'
                echo "----------- unit test completed ----------"
            }
        }
    }

    post {
        always {
            echo "Build finished: ${currentBuild.currentResult}"
        }
    }
}

