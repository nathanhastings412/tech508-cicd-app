## Deploying changes after merge

1. `nathan-job3-dc-deploy`
2. description
3. 5 max builds
4. build triggers after job 2
5. Add ssh agent
   - Select the key pair that is paired with aws, or add that key pair then select it
6. build execute shell
7. The following code needs amending to make it work: ssh -o StrictHostKeyChecking=no ubuntu@ec2-108-129-195-213.eu-west-1.compute.amazonaws.com "echo connected"

rsync -avz --delete "$WORKSPACE/" ubuntu@ec2-108-129-195-213.eu-west-1.compute.amazonaws.com:/home/ubuntu/repo

ssh ubuntu@ec2-108-129-195-213.eu-west-1.compute.amazonaws.com << 'EOF'
	cd repo/app
    npm install
    pm2 stop all
    pm2 start app.js
EOF
8. save, push a change