pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('Git Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'git \'https://github.com/parasahirwar/my-repo.git\'']]])kout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'Git', url: 'https://github.tycoelectronics.net/HappiestMindControlTower/backendService.git']]])
            }
        }
        stage('Maven Build') {
            steps {
                sh """
                    echo "Build Stage testing"
                    pwd && ls
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                    sh "${mvnHome}/bin/mvn clean package"
                    ls
                  """
            }
        }
        stage('Archive') {
            steps {
               archiveArtifacts artifacts: 'webapp/target/*.war, server/target/*.jar',
               fingerprint: true,
               onlyIfSuccessful: true
            }
           
        }
	}
}	
