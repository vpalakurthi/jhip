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
    
    stage('deploy') {
        sh "kubectl apply -f jhip/deployment.yml --kubeconfig=kubeconfig""
    }   		
}
