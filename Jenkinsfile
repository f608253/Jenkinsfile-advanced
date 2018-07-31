pipeline {
       agent any
       tools {
            maven 'maven'
            jdk 'JAVA_HOME'
}
       stages {
            stage ('compile stage') {
                 steps {
                      sh 'echo $(PATH)'
                      sh 'echo $(M2_HOME)'
                      sh  'mvn -X clean compile'
           }
      }
            stage ('Testing stage') {
                steps {
                sh 'mvn -X test'
           }
      }
            stage ('Deployment stage') {
                   steps {  
            sh 'mvn -Dmaven.test.failures.ignore=true install'
      }
            
            post {
                success {
                junit 'target/surefire-reports/**/*.xml'
          
          }
      
        }
     }
  }
}
