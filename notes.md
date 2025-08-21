## Create Jenkins Job and observe its output
1. Add new
2. nathan-first-project
3. discord old builds
4. max number of 5
5. build steps
6. execute shell
7. uname -a
8. build now
9. build history
10. select build in build history
11. console output
12. look at output of uname -a command

## Configure a second job to run after first in Jenkins
1. go to job 1
2. configure
3. post-build actions
4. build other projects
5. add jobs to build
6. trigger only if build is stable
7. in console output, it declares if it is triggering new build

## Generate ssh key and add deploy key to github repo
1. `cd .ssh`
2. `ssh-keygen -t rsa -b 4096 -C "nathanhastings412@gmail.com"`
3. BE VERY CAREFUL when typing name - cant do backspaces
4. no password
5. `ls` to confirm it is there
6. go to your github repo > settings > security > deploy keys > add deploy key
7. name it the same name
8. cat public key
9. copy and paste it into github key box




