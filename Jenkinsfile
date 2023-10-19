pipeline{
agent any

options{
buildDiscarder(logRotador(numToKeepStr:'5'))
}

environment{
DOCKERHUB_CREDENTIALS = credentials('assilenouT')
}

stage{
stage('Build'){
step{
sh 'docker build -t assilenouT/jenkins-docker-assilenou.'
}
}

stage('Login'){
steps{
sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u
$DOCKERHUB_CREDENTIALS_USR --password-stdin'
}
}

stage('Push'){
steps{
sh 'docker push assilenouT/jenkins-docker-assilenou'
}
}
}

post{
always{
sh 'docker logout'
}
}
