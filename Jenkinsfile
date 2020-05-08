pipeline{

    agent any

    stages {

        stage ('Compile Stage') {

            steps {

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