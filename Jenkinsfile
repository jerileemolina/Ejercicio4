pipeline{
    agent {
        kubernetes {
            defaultContainer 'jdk'
            yaml '''
apiVersion: v1
kind: Pod
spec:
    securityContext:
        runAsUser: 1001
    containers:
    - name: jdk
      image: docker.io/eclipse-temurin:18.0.2.1_1-jdk
      command:
        - sleep
      args:
        - infinity
    - name: podman
      image: quay.io/containers/podman:v4.2.0
      command:
        - sleep
      args:
        - infinity
      securityContext:
        runAsUser: 0
        privileged: true

'''

        }
    }

    stages {
      stage("Prepare environment") {
          steps {
            echo ' -=- prepare build environment -=-'
            sh 'java -version'
            container('podman') {
            sh 'podman --version'

            }
          }

      stage("Compile") {
          steps {
            echo ' -=- compile code -=-'
          }
      }

      stage("Unit tests") {
          steps {
            echo ' -=- execute unit tests -=-'
          }
      }

      stage("Mutation tests") {
          steps {
            echo ' -=- execute mutation tests -=-'
          }
      }


      stage("Dependency vulnerarability scans") {
          steps {
            echo ' -=- dependency vulnerability scans -=-'
          }
      }


      stage("Code Inspection") {
          steps {
            echo ' -=- Code Inspection -=-'
          }
      }

      stage("Package") {
          steps {
            echo ' -=- Package -=-'
          }
      }

      stage("Build & push container image") {
          steps {
            echo ' -=- build & push container image -=-'
          }
      }

      stage("Run ephemeral test environment") {
          steps {
            echo ' -=- run ephemeral test environment -=-'
          }
      }

      stage("Integration tests") {
          steps {
            echo ' -=- execute integration tests -=-'
          }
      }

      stage("Performance tests") {
          steps {
            echo ' -=- execute performance tests -=-'
          }
      }

      stage("Promote container image") {
          steps {
            echo ' -=- promote container image -=-'
          }
      }

      post {
          always {
              echo 'cleaning up resources'
              container('aks') {
                  withCredentials ([
                        usernamePassword(
                            credentialsId:'sp-terraform-credentials',
                            usernameVariable:'AAD_SERVICE_PRINCIPAL_CLIENT_ID',
                            passwordVariable: 'AAD_SERVICE_PRINCIPAL_CLIENT_SECRET')]) { 
                      sh "kubectl delete pod $(TEST_CONTAINER_NAME)"
                      sh "kubectl delete service $(TEST_CONTAINER_NAME)"
                      sh "kubectl delete service $(TEST_CONTAINER_NAME)-jacoco"
                            
                            
                            }

                      
                        
              }
            }
          }
        }
      }
    }