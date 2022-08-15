@Library('jenkins-shared-library')
def gv
pipeline {
    agent any
    tools {
        maven 'maven-3.6'
    }
    parameters{
        text(name:"version" , defaultValue:"" , description : "")
    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("test") {
            steps {
                script {
                    echo "testing application on ${BRANCH_NAME}"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    buildJar "haythambammou/my-repo:jma-2.0"   
                }
            }
        }
        stage("build image") {            
            steps {
                script {
                    buildImage()
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    gv.deployApp()
                }
            }
        }
    }
}