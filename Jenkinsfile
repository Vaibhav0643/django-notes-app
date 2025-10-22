
pipeline{
    agent any
    
    stages{
        stage("Code clone"){
            steps{
                sh "whoami"
            echo "Cloning the Code"
            git url: "https://github.com/Vaibhav0643/django-notes-app.git", branch: "main"
            echo "Code cloning successful"
                
            }
        }
        stage("Code Build"){
            steps{
            echo "Building the notes app code"
            sh "docker build -t notes-app:latest ."
            }
        }
        stage("Deploy"){
            steps{
                echo "Deploying code ...."
                sh "docker run -d -p 8000:8000 notes-app:latest"
            }
        }
        
    }
}