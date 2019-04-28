properties([pipelineTriggers([githubPush()])]) 
node('linux'){
    stage('Unit Tests'){
        git 'https://github.com/mddatascience/java-project.git'
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
}
