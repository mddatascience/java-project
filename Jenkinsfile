properties([pipelineTriggers([githubPush()])]) 
node('linux'){
    stage('Build'){
        git 'https://github.com/mddatascience/java-project.git'
        sh "ant"
    }
    
    stage('Unit Tests'){
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
}
