pipeline {
    agent {
      docker {
            image 'maven:3-alpine'
            args '-v C:\Users\Irfan_Ilyas\.m2:/root/.m2'
        }
    }
    stages {
        
        stage ('Compile Stage') {

            steps {
                    sh 'mvn --version'
                    sh 'mvn clean compile'
            }
        }

        stage ('Testing Stage') {

            steps {
                    sh 'mvn test'
            }
        }

    }
}
