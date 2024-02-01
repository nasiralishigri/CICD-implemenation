# CICD-implemenation

  #  Create a folder on github or on your project directory

    .github/workflows
  #   Create a file name with ci-cd.yml

    Create file to save the instruction of deployment on github

  #  Update This inscturction to .yml file


    name: Node.js CI/CD

    on:
     push:
       branches:
         - main

    jobs:
     build:
      runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Install dependencies
      run: npm install

    - name: Build
      run: npm run build

    - name: Deploy to Ubuntu Server
      uses: appleboy/ssh-action@master
      with:
        host: ${{ secrets.SERVER_HOST }}
        username: ${{ secrets.SERVER_USERNAME }}
        key: ${{ secrets.SERVER_SSH_KEY }}
        script: |
          cd /path/to/your/node/app
          git pull origin main
          npm install
          pm2 restart app # Assuming you use PM2 for process management


  Update your branch if it's not main branch.
  Update your ubuntu version according to your ubuntu system
 Update your project path in scripts like cd /home/ubuntu/swapping

 # Add your environment variables in github
     
 
  

    
