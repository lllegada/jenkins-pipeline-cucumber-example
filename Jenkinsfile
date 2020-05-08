pipeline{

    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }

    stages {

        stage ('Compile Stage') {

            steps {
                sh 'mvn clean install'
                sh 'mvn -B -DskipTests clean package'

            }
        }
    stage ('Test Stage') {

            steps {

                sh 'mvn test'

            }
        }


        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'

            }

        }

    }

}