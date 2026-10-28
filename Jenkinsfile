
pipeline {
    agent any

    environment {
        KUBECTL = 'D:\\DockerApp\\resources\\bin\\kubectl.exe'
        KUBECONFIG = 'C:\\Users\\POOVARASAN\\.kube\\config'
    }

    stages {
        stage('Deploy Application') {
            steps {
                bat '"%KUBECTL%" apply -f deployment.yaml'
            }
        }

        stage('Update Image') {
            steps {
                bat '"%KUBECTL%" set image deployment/rolling-app nginx=nginx:stable'
            }
        }

        stage('Verify Rolling Update') {
            steps {
                bat '"%KUBECTL%" rollout status deployment/rolling-app --timeout=120s'
                bat '"%KUBECTL%" rollout history deployment/rolling-app'
                bat '"%KUBECTL%" get deployments'
                bat '"%KUBECTL%" get pods'
            }
        }
    }
}
