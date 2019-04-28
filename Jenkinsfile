properties([pipelineTriggers([githubPush()])]) 
node('linux'){
    stage('Unit Tests'){
        git 'https://github.com/mddatascience/java-project.git'
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    stage('Build'){
        sh "ant -f build.xml -v"
    }
    
    stage('Deploy'){
        sh "aws s3api create-bucket --bucket my-bucket --region us-east-1"
        
    }
    
}
