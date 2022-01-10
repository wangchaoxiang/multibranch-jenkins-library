pipeline {
  agent any
  stages {
    stage("Hello") {
      steps {
        echo "Hello"
      }
    }
    stage("Build") {
      steps {
        echo "Build"
      }
    }
    stage("Test") {
      steps {
        echo "Test"
        sh '''cat README.md'''
      }
    }
  }
  post {
        always {
            script {
                println "Begin Run multibranch-sample-app-begin..."
                jobB = build job: 'multibranch-sample-app-begin', propagate: false, wait: true, 
                    parameters: [
                        string(name:'TestVersion', value:"1.0.0")                                                                    
                    ]
                println "End Run multibranch-sample-app-begin..."
            }
        }
    }
}