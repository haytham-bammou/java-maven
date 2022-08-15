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
                    buildJar()   
                }
            }
        }
        stage("build image") {            
            steps {
                script {
                    buildImage "${params.version}"
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