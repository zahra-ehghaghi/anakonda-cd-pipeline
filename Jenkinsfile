pipeline {
    agent any
    parameters{
        string(name: "ENV" ,defaultValue: "", trim: true, description: "Environment name")
        string(name: "IMAGE_NAME" ,trim: true, description: "Image repository")
        string(name: "IMAGE_TAG" ,trim: true, description: "Image tag")

    }
    stages {
        stage("Prepare") {
            steps {
                echo "Build stage."
            }
        }
        stage("Deploy") {
         
            steps {
		withCredentials([file(credentialsId: 'k3s-user', variable: 'KUBECONFIG')]) {
		script
		{
      			if ("$params.ENV" == "deployment") {
				sh "sed -i 's/IMAGE_NAME/${IMAGE_NAME}/g' dev/kustomozation.yml
                                sh "sed -i 's/IMAGE_TAG/${IMAGE_TAG}/g' dev/kustomozation.yml

				sh "kubectl  apply -k dev" 
			}
		}
		}
            }
        }
    }
}
