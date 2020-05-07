pipeline {
    agent {
                            def secrets = [
                           [path: 'secret/testing', engineVersion: 2, secretValues: [
                              [envVar: 'testing', vaultKey: 'value_one'],
                              [envVar: 'testing_again', vaultKey: 'value_two']]],
                           [path: 'secret/another_test', engineVersion: 2, secretValues: [
                              [vaultKey: 'another_test']]]
                           ]

                     def configuration = [vaultUrl: 'http://localhost:8200',
                         vaultCredentialId: 'my-vault-cred-id',
                         engineVersion: 1]
    }
    stages {
        
        stage ('Secret Retrieval') {
        
            steps {
              
            withVault([configuration: configuration, vaultSecrets: secrets]) {
                sh 'echo $testing'
                sh 'echo $testing_again'
                sh 'echo $another_test'
             }  
            }
        }
        
        stage ('Compile Stage') {

            steps {
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
