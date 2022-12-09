pipeline{
    agent any
    tools{
         maven 'Maven'
    }

    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    ech0 "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat8(credentialsId: '4626fb53-0fcf-47a7-85ad-a6bbc1b29f03', path: '', url: 'http://54.234.176.125:8090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
