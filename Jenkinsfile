pipeline {
         agent any
         tools {nodejs "NodeJS"}

    stages {
        stage("Code checkout") {
            steps {
              
              git 'https://github.com/rbkore/node-unit-tests.git'
                  
            }
              }
         stage('Code Quality') {
                   steps {
                       script {
                          def scannerHome = tool 'sonar_scanner';
                          withSonarQubeEnv("sonar_server") {
                          sh "tool("sonar_scanner")}/bin/sonar-scanner"
                                       }
                               }
                           }
                        }

         stage("Install Dependencies") {
                                  steps {
                                        sh "npm install"

                                       }
                                }

         stage("unit Test") {
                            steps {
                                sh "npm test"

                              }
                        }
             }
     }

