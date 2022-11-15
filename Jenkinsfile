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
        }
      }
    }