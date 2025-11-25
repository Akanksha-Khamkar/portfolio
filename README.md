# portfolio

# 1. Initialize a git repo (if not already a git repo)
git init

# 2. Check files
git status

# 3. Create a .gitignore (optional) to ignore files like node_modules, .env
# Use your editor to create .gitignore, then:

# 4. Stage files for commit (all files)
git add .

# 5. Commit
git commit -m "Initial commit"

# 6. Add remote (replace with your repository URL)
git remote add origin https://github.com/youruser/my-repo.git
# OR for SSH:
# git remote add origin git@github.com:youruser/my-repo.git

# 7. Push to GitHub (set upstream and push branch main)
git branch -M main                # optional: rename current branch to main
git push -u origin main




git init
git add .
git commit -m "first commit"
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main




git clone repository name

git status

git add index.html
git add about.html
git add README.md

git commit -m "intially add 2 page website & README.md file"



Jenkins Pipeline (Example Jenkinsfile):

pipeline {
 agent any
 environment {
 DEPLOY_DIR = 'C:\\inetpub\\wwwroot' // IIS web root folder
 }
 stages {
 stage('Checkout') {
 steps {
 echo 'Cloning project from GitHub...'
 git branch: 'main', url: 'https://github.com/Akanksha-Khamkar/portfolio.git'
 }
 }
 stage('Build') {
 steps {
 echo 'Build Step: Check files in workspace'
 bat 'dir'
 }
 }
 stage('Deploy') {
 steps {
 echo "Deploying Home.html to IIS folder"
 // Directly copy Home.html to webserver root
 bat "xcopy /Y home.html ${DEPLOY_DIR}\\"
 }
 }
 stage('Run HTTP Server (Optional Test)') {
 steps {
 echo 'Skipping HTTP server (use IIS instead)'
 // For testing, you can use: bat 'python -m http.server 8000'
 }
 }
 }
 post {
 success {
 echo 'Pipeline finished successfully! Visit: http://localhost/Home.html'
 }
 failure {
 echo 'Pipeline failed! Check build logs.'
 }
 }
}}
