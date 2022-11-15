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

          }
        }
      }