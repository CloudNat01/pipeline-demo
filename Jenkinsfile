node {
    stage("Git Clone"){

        git credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/CloudNat01/pipeline-demo.git'
    }
    
    stage("Docker build"){
        sh 'docker version'
        sh 'docker build -t sample-loveth .'
        sh 'docker image list'
        sh 'docker tag sample-loveth cloudnat/sample-loveth:latest'
    } 
    
    stage("Docker Login"){
        withCredentials([string(credentialsId: 'DOCKER_HUB_PASSWORD', variable: 'PASSWORD')]) {
            sh 'docker login -u cloudnat -p $PASSWORD'
        }
    } 
    
    stage("Push Image to Docker Hub"){
        sh 'docker push  cloudnat/sample-loveth:latest'
    }
}
