echo "Petclinic Pipe"

pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/wazolee/course3-jenkins-gs-spring-petclinic'
            }
        }
        stage("build"){
            steps{
                sh "mvn package"
            }
        }
        stage("capture"){
            steps{
                archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
                jacoco()
                junit '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    post{
        always{
            sh "ls"
        }
        
    }
}
