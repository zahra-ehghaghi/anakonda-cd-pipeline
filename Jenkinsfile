pipeline {
    agent any
    parameters{
	string(name: "PROJECT" ,trim: true, description: "P roject name")
        string(name: "ENV" ,defaultValue: "", trim: true, description: "Environment name")
        string(name: "IMAGE_NAME" ,trim: true, description: "Image repository")
        string(name: "IMAGE_TAG" ,trim: true, description: "Image tag")
        string(name: "NAMESPACE" ,trim: true, description: "Kubertenese target namespace")

    }
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
