pipeline{
    agent {
        kubernetes {
            defaultContainer 'jdk'
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
  }
}