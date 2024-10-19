// This Jenkinsfile is for Eureka Deployment 

pipeline {
    agent {
        label 'k8s-slave'
    }
    tools {
        maven 'Maven-3.8.8'
        jdk 'JDK-17'
    }
    environment {
        APPLICATION_NAME = "eureka" 
    }
    stages {
        stage ('Build') {
            steps {
                echo "Building the ${env.APPLICATION_NAME} Application"
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage ('Sonar') {
            steps {
                echo "Starting Sonar Scan"
                mvn  sonar:sonar \
                -Dsonar.projectKey=i27-eureka \
                -Dsonar.host.url=http://34.55.191.104:9000 \
                -Dsonar.login=squ_3bb3697d56549a4ac332f75062914e055020d5cf
            }
        }
    }
}


