pipeline {
    agent { label 'slave1' } 
    stages {
        stage('checkout1') {
            steps {
                sh 'https://github.com/malteshig/hello-world-war.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
       stage('Push artifacts into artifactory') { 
           steps { 
               rtUpload ( 
                   serverId: 'migartifactory', 
                   spec:     '''{ 
                       "files": [ 
                           { 
                               "pattern": "*.war", 
                                "target": "example-repo-local/" 
                            }  
                            ] }'''
                        )	 }	}
    }
}
