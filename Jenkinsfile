pipeline {
    agent any

    stages {
        stage('Checkout GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/madhandog24/emergencyaiii.git'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                withEnv(['KUBECONFIG=C:\\Users\\karan\\.kube\\config']) {
                    bat '"C:\\Users\\karan\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\kubectl.exe" apply -f deployment.yaml'
                    bat '"C:\\Users\\karan\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\kubectl.exe" apply -f service.yaml'
                    bat '"C:\\Users\\karan\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\kubectl.exe" rollout status deployment/emergency-ai'
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withEnv(['KUBECONFIG=C:\\Users\\karan\\.kube\\config']) {
                    bat '"C:\\Users\\karan\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\kubectl.exe" get deployments'
                    bat '"C:\\Users\\karan\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\kubectl.exe" get services'
                }
            }
        }
    }
}