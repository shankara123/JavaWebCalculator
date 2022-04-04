pipeline{
    agent any
    stages{
        stage('checkout for scm'){
            steps{
            git branch:'html_code',
                credentialsId:'709fc51a-19d4-4a49-8838-3049283fabaf',
                url:'https://github.com/shankara123/JavaWebCalculator.git'
            }
        }
        stage('build the artifact'){
            steps{
            sh'''
            mvn clean
            '''
            }
        }
        stage('Testing'){
            steps{
                sh'''
                mvn test
                '''
            }
        }
        stage('deploy into nexus'){
            steps{
            sh'''
            mvn deploy
            '''
            }
        }
        stage('deploy into tomcat'){
            steps{
                build job: 'download_deploy'
            }
        }
    }
}
