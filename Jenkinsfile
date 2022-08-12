pipeline {
    agent any
    tools {
        maven 'maven-3.6'
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
             when{
                    expression {
                        BRANCH_NAME == "master"       
                    }
                }
            steps {
                script {
                    gv.buildJar()
                }
            }
        }
        stage("build image") {
             when{
                    expression {
                        BRANCH_NAME == "master"       
                    }
                }            
            steps {
                script {
                    gv.buildImage()
                }
            }
        }
        stage("deploy") {
             when{
                    expression {
                        BRANCH_NAME == "master"       
                    }
                }
            steps {
                script {
                    gv.deployApp()
                }
            }
        }
    }
}