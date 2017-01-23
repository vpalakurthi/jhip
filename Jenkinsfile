

node {
    stage('checkout') {
        checkout scm
    }

    stage('clean') {
        sh "./mvnw clean"
    }

    stage('packaging') {
        sh "./mvnw package -Pprod -DskipTests"
    }
    
    stage('deploy') 
    withKubernetes(serverUrl: "https://192.168.42.33:30000', credentialsId:'kubeadmin'){
        sh "kubectl apply -f jhip/deployment.yml --kubeconfig=kubeconfig"
    }   		
}
