pipeline {
    agent any
    stages {
        stage("Prepare") {
            steps {
                echo "Build stage."
            }
        }
        stage("Deploy") {
            steps {
                echo "Build stage."
		withCredentials([file(credentialsId: 'k3s-user', variable: 'KUBECONFIG')]) {
			sh "kubectl  apply -k deployments/mysql" 
                        sh "kubectl  apply -k deployments/anakonda" 

		}
            }
        }
    }
}