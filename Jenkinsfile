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
        sh "aws s3 cp dist/rectangle-${BUILD_NUMBER}.jar s3://jenkins-bucket-mjd"
    }
    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIA5EATQOEHTAHGHCZS', credentialsId: 'AWS user for Jenkins', secretKeyVariable: '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']]) {
            sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1' 
        }	  
    }
    
}
