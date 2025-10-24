pipeline{
    agent any
    tools {
        maven "maven 3.9.6"
    }
    stages{
        stage('git configuration'){
            steps{
                git branch: 'development', url: 'https://github.com/git-pathan/maven-webapplication-project-kkfunda.git'
            }//steps ending
        }//stage ending
        stage('maven build'){
            steps{
                sh "mvn clean package"
            }
        }
        stage('sonar'){
            steps{
                sh "mvn sonar:sonar"
            }
        }
        stage('nexus'){
            steps{
                sh "mvn deploy"
            }
        }
       stage('tomcat') {
    steps {
        sh """
            curl -u pathan:password \\
            --upload-file target/maven-web-application.war \\
            "http://3.91.189.67:8080/manager/text/deploy?path=/maven-web-application&update=true"
        """
    }
}

    }//stages ending
}//pipeline ending
