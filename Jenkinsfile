pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn clean package'
                }
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    cd 'C:\Users\ThisPc\cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD'
                    cd 'C:\Users\ThisPc\cf push'
                }
            }

        }

    }

}