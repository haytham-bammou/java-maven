pipeline {
    agent any
    tools {
        maven 'maven-3.6'
    }
    stages {
        stage("build jar") {
            steps {
                script {
                    echo "building the app ..." 
                    sh "mvn package"
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building the app ..." 
                    //sh "mvn package"
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId :'github_credentials' , passwordVariable:'PWD' , usernameVariable:'USER')]){
                        echo "deploying the app ..."  
                        echo "${USER} ${PWD}"
                    }
                }
            }
        }
    }
}