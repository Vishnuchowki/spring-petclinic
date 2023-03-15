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
                    branch: 'sprint_1'
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
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/spring*.jar',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
        
    }
}