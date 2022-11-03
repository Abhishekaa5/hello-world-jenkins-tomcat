pipeline {
    agent any

    stages {
//         stage('chceckout') {
//             steps {
//                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Abhishekaa5/hello-world-jenkins-tomcat.git']]])
//             }
//         }
        stage('clean'){
            steps{
                sh "mvn -f webapp/pom.xml clean"
            }
        }
        stage('install'){
            steps{
                sh "mvn -f webapp/pom.xml install"
            }
        }
        stage('deploy'){
            steps{
               sshagent(credentials: ['ec2-user'], ignoreMissing: true) {
                sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@52.66.82.14:/home/ec2-user/apache-tomcat9/webapps"
}
            }
        }
    }
}
