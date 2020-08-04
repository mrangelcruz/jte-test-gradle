pipeline{
    agent {
        label "docker_build"
    }
    stages{
        stage('build'){
            steps{
                echo "... build step ..."
                // sh 'chmod +x gradlew'
                // sh './gradlew clean build -DskipTests=true'
                // archiveArtifacts artifacts: 'build/libs/**/*.jar'
            }            
        }
        stage('test'){
            steps{
                //sh './gradlew test'
                echo "... test step ..."
            }
            post {
                always {
                    //junit 'build/test-results/**/*.xml'
                    //archiveArtifacts artifacts: 'build/reports/jacoco/**/*.xml'
                    echo "...POST test step ..."
                }
            }            
        }
        stage('approve'){
            when{
                branch 'master'
            }
            agent none
            steps{
                script{
                    timeout(time: 5, unit: 'SECONDS'){
                        input message: 'APPROVE OR NOT', submitter: 'admin'
                    }
                }
            }
        }
        stage('deploy'){
            when{
                branch 'master'
            }
            steps{
                echo "Pending Implementation"
            }
        }
    }
}
