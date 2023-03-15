pipeline {
    agent { label 'NODE_3' }
    triggers { pollSCM ('* * * * *') }
    //parameters {
    //    choice(name: 'MAVEN_GOAL', choices: ['package', 'install', 'clean'], description: 'Maven Goal')
    //}
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/Vishnuchowki/spring-petclinic.git',
                    branch: 'develop'
            }
        }
        stage('package') {
            tools {
                jdk 'JAVA_17_UBUNTU'
            }
            steps {
                sh "./mvnw package"
            }
        }
        
    }
}