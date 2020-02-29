pipeline{
    triggers {
        GenericTrigger (causeString: 'blog is updated', regexpFilterExpression: '', regexpFilterText: '', token: 'ibizaGithub')
    }

    agent {
        label 'host'
    }

    stages {
        stage('pull Ibiza directory') {
            steps{
                // some block
                sh script: '''
                    cd /home/wanderlust/blog/Ibiza
                    git pull
                '''
            }
        }
        stage('push blog to github'){
            steps{
                sh script: '''
                    cd /home/wanderlust/blog/Ibiza
                    ./pushBlog.sh
                '''
            }
        }
    }
}