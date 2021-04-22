pipeline {
         agent any
         tools {nodejs "nodejs"}

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
                                   bat "${tool("sonar_scanner")}/bin/sonar-scanner.bat"
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
         
         post {
                  always {
                           emailext (
                                    attachLog: true,
                                    subject: "obname",
                                    body:  "emailbody"
                                    compressLog: false,
                                    recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                                             to: 'rbkore123@gmail.com' 
                           )
                  }
                  }
                  
                                    
     }

