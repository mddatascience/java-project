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
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAI54NTZ55YRQZQV2A', credentialsId: 'admin', secretKeyVariable: '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']]) {
            sh 'aws s3api create-bucket --bucket jenkinsbucket --region us-east-1' 
        }
    }
    
}
