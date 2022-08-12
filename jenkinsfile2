def gv

pipeline {
    agent any
    environment {
        NEW_VERSION = "1.3.0"
    }
    parameters{
        choice(name:"VERSION" , choices:["1.0.0" , "1.0.1" , "1.0.2"] , description:"")
        booleanParam(name:"executeTest" , defaultValue:true , description : "")
    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("test"){
            when {
                expression {
                    params.executeTest
                }
            }
            steps {
                echo "executing tests"
            }
        }
        stage("build jar") {
            steps {
                script {
                    echo "building jar"
                    echo "building image version ${NEW_VERSION}"
                    //gv.buildJar()
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building image ${params.VERSION}"
                    //gv.buildImage()
                }
            }
        }
        stage("deploy") {
            steps {
                echo "deploying image "
            }
        }
    }   
}