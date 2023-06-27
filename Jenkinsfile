pipeline {
    agent any
    stages {
        stage('checkout1') {
            steps {
                sh 'git clone https://github.com/malteshig/hello-world-war.git'
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
