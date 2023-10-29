pipeline {
    agent any

    stages {
        stage('gitcheckout') {
            steps {
checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mahendarreddychilumula/nodejsapplicationtest.git']])
            }
        }
    stage('docker build'){
        steps{
            sh 'docker build ./login-registration-server-node -t mahendarreddychilumula/nodeapp:latest'
        }
            
        }
    stage('docker push'){
        steps{
            sh 'echo "7075873342Ma@" | docker login -u mahendarreddychilumula --password-stdin'
            sh 'docker push mahendarreddychilumula/nodeapp:latest'
        }
    }
    stage('sshlogin'){
        steps{
            withCredentials([sshUserPrivateKey(credentialsId: 'manupem', keyFileVariable: 'manupem', usernameVariable: 'manu')]) {
         sh ''' ssh -o StrictHostKeyChecking=no -i $manupem ubuntu@ec2-3-236-114-230.compute-1.amazonaws.com && echo "7075873342Ma@" | docker login -u mahendarreddychilumula --password-stdin && docker run -d -p 8090:5000 mahendarreddychilumula/test:v1
                // docker ps -a
                // echo $USER
                '''

}
        }
    }
    }
    }

