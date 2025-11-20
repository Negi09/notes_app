@Library('Shared')_
pipeline{
    agent { label 'dev-server'}
    
    stages{
        stage("Code clone"){
            steps{
                sh "whoami"
                script{
                    
            clone("https://github.com/Negi09/notes_app.git","main")}
            }
        }
        stage("Code Build"){
            steps{

            script{           dockerbuild("notes-app","latest")
            }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                dockerpush("dockerHubCreds","notes-app","latest")}
            }
        }
        stage("Deploy"){
            steps{Script{
                deploy()
            }}
        }
        
    }
}
