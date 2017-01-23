
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
        sh "kubectl exec --namespace=default apply -f jhip/jhip-deployment.yml"
    }   		
}
