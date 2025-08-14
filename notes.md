## Create Jenkins Job and observe its output
1. add new
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

## Create a new Jenkins job
1. new job
2. nathan-job1-ci-test
3. freestyle project
4. give description
5. discard old builds > max 5
6. select github project
7. go to github repo > code
8. copy https url
9. paste url into github project
10. remove `.git/` and add `/`
11. go to Source Code Management
12. Select Git
13. find the SSH URL, copy and paste it into repository URL
14. credentials > add > Jenkins
15. Kind > SSH Username with private key
16. ID - private key name
17. description 
18. username - private key name
19. private key > enter directly
20. cat private key to screen in gitbash
21. copy and paste ALL OF IT to the box in jenkins (INCLUDING THE HEADER AND FOOTER AND ALL OF THE DASHES)(FROM THE FIRST CHARACTER TO THE LAST)
22. Add
23. select your credentials
24. branch specifier - `*/main`
25. Go to build environment
26. select provide Node and npm bin/ folder to PATH
27. specify node version 20
28. Go to build steps > add build step > execute shell (these commands will run from the root of the repo on the worker node)
29. cd into app folder
30. `npm install`
31. run a unit test `npm test`

## set up a webhook
1. github repo > settings > webhooks > add webhook
2. this is the format for the payload url but it needs my own ip address
3. add webhook

1. go to job1
2. configure
3. build triggers
4. select github hook trigger for GITScm polling

1. open new git bash window
2. go to the new repo
3. nano README.md
4. Test webhook timestamp
5. git add .
6. git commit -m "change readme"
7. git push origin main
8. should see something trigger on jenkins
9. then change the branch
10. git branch dev
11. git switch dev
12. go into job 1
13. configure
14. branch specifier change to `*/dev`
15. save and do a git push