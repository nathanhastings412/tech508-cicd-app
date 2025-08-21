## Merging branches after test
 
Prerequisite: Job 1 working (test changes)

Job 2 is merging the changes

1. `nathan-job2-ci-merge`
2. give description
3. Discard a max of 5 old builds
4. link to github project using github repo https URL
5. In Source Code Management
   - link to github project using github repo SSH URL
   - Select your credentials
6. Select branches to build
   - `*/main` - select the branch you are merging to
7. Additional behaviours > merge before build
   - name - origin
   - branch to merge to - main
   - strategy - default
   - fast-forward mode - --ff
8. Build environment > SSH agent
   - select your credentials
9. Build steps > add build step > execute shell
   - Set Git commit identity
     - `git config --global user.name "nathanhastings412"`
     - `git config --global user.email "nathanhastings412@gmail.com"`
   - Switch to main branch
     - `git checkout main`
   - Make sure main is up to date
     - `git pull origin main`
   - Merge dev into main
     - `git merge origin/dev --no-ff -m "Merge dev into main via Jenkins"`
   - Push updated main branch
     - `git push origin main`
10. Save and apply
11. Post-build actions > git publisher
    - push only if build succeeds
    - merge results
    - force push
    - Branches
      - push `main`
      - target remote name `origin`
12. In Job 1 > post-build actions > add post-build action > build other projects
    - select job2
    - trigger only if build is stable
13. now when you push changes to your dev branch locally, jenkins pulls those changes from that github branch and merges them into the main branch.