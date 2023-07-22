pipeline {
    agent { label 'JDK_17'}
    options{
        timeout(time: 15, unit: 'MINUTES') 

    }
    triggers { pollSCM('* * * * *') }
    tools {
        jdk 'JDK_17'
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/divyakothuru311/Jenkins',
                branch 'main'
                
                            
            }
        }    
        stage('build and package') {
            steps {
                sh script : 'mvn package'

            }
        }    
        stage('report') {
            steps {
                archiveArtifacts artifacts: '**/target/springpetclinic-*.jar'
                junit testResults: '**/target/surefire-reports/TEST-*.xml'
            }
        }
    }
}
    
    
