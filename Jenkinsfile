#!groovy

node {
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


def mvn(args) {
    sh "${tool 'Maven 3.x'}/bin/mvn ${args}"
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
