pipeline{
    triggers {
        GenericTrigger (causeString: 'blog is updated', regexpFilterExpression: '', regexpFilterText: '', token: 'ibizaGithub')
    }

    options {
        disableConcurrentBuilds()
    }

    agent {
        label 'host'
    }

    stages {
        stage('pull Ibiza directory') {
            steps{
                ws ('/home/wanderlust/blog/Ibiza') {
                    sh script: '''
                        git pull
                        git secret reveal -f
                        git submodule update --recursive
                    '''
                }
            }
        }
        stage('push blog to github'){
            steps{
                ws('/home/wanderlust/blog/Ibiza') {
                    sh script: '''
                        ./pushBlog.sh
                    '''
                }
            }
        }
    }
}
