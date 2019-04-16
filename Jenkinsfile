node {
stage('git scm'){
  git credentialsId: '6ed221e2-1344-4cda-80f4-7b935c4f5b53', url: 'https://github.com/saikrishna345/discoveryservice.git'
    }
stage ('mvn package'){
    sh 'mvn clean package'
}
stage('docker build'){
   sh 'docker build -t saidoc47/discovery-microservice-server:2.0.0 .'
}
stage('docker image'){
   sh  'docker login -u saidoc47 --password-stdin < ~/Spring-boot-with-docker/discovery-microservice-server/dockercredintials.txt' 
    sh 'docker push saidoc47/discovery-microservice-server:2.0.0'
}
stage('docker in dev-server'){
    sh 'docker run -p 1414:1111 -d saidoc47/discovery-microservice-server:2.0.0'
}
 stage('Email')  {
           mail bcc: '', body: "${env.JOB_NAME} : ${env.BUILD_NUMBER} is ${currentBuild.currentResult}  ", cc: '', from: '', replyTo: '', subject: 'Jenkins pipeline status', to: 'saikrishnamulkanuri5@gmail.com'
        }
}

