pipeline {
    
  stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
       stage('Deploy') { 
            steps {
                //Got from Pipeline syntax in Jenkins
                 step([$class: 'KubernetesEngineBuilder', 
                        projectId: "hello-sky",
                        clusterName: "test",
                        zone: "us-central1-c",
                        manifestPattern: 'k8s/test/',
                        credentialsId: "service-account-key",
                        verifyDeployments: true])
            }
        }
    }
}
