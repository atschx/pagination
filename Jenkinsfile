pipeline {
  agent any
  tools {
    jdk 'jdk8'
    maven 'Maven 3.3.9'
  }
  stages {
    stage('initialize') {
      steps {
        sh '''echo PATH = ${PATH}
echo M2_HOME = ${M2_HOME}
mvn -version'''
      }
    }
    stage('checkout'){
      git credentialsId: '0fe280b7-d857-4689-b649-0b612417f51e', url: 'https://github.com/atschx/pagination.git'
    }
    
    stage('package'){
      mvn 'clean package'
    }
    
    stage('test'){
      deploy('test')
      testAlive('')
    }
    
    stage('production'){
      deploy('prod')
      testAlive('')
    }
  }
}

def deploy(env) {
    dir('target') {
        sh "mkdir -p envs/$env"
        sh "cp pagination.jar envs/$env"
    }
}

def testAlive(url) {
    sleep 3
}
