# ####### #   
#   Git   #
# ####### #

- developed by Linux 
- distributed Version Control sys 
- can be work offline (locally) 
- files stored in SHA-1 (Secure Hash Algo) 
- properties of SHA: 
    1. fixed length hash 
    2. deterministic o/p is same for same input 
    3. avalanche effect -for minor change, entire hash changes 
- compressed format 
- 3 stages: 
    1. Working dir 
    2. Stagging Area (or Caching or Index area) 
    3. Git/Local dir 
- 2 types cmd: 
    1. Porcelain cmd - git add, git commit, git branch, git status 
    2. Plumbing cmd - core commands(never used in project)    
    git cat-file -t 5t84asd #to know the type of SHA 
    git cat-file commit 5t84asd  #gives what's inside in given hash 
- 2 ways to add remote to local repo 
    1. add remote 
        > git init 
        > git remote add origin <urlFromGitHubHttpsOne.git> > git fetch origin main 
        > git merge origin/main 
    2. clone 
        > git clone <url.git>

# Commands 
1. git init #create .git folder ie. local repo. Never mess with it 
2. git config --list 
    i. global level -> user.name and user.email -> commit purpose 
    ii. system level 
    iii. local level 
3. git config --global user.name johny (or for local lvl that apply to current folder only) git config user.name john 
4. git config --global user.email xyz@gmail.com 
5. git config --list --global 
6. git status 
7. git add fileName  #add file to stagging area
8. git rm --cached fileName  #to unstage area 
9. git add .  #or git add * to add all files in staging area 
10. git commit -m "msg here"  #commit the changes to local repo 
11. git log  #gives SHA (or check-sum value of commit), author and date 
12. git log --oneline #short o/p only 7 char of SHA val display 
13. git log -2 #display recent 2 commits
14. git log -p #display changes done for every commit 
15. git log --grep="matchPattern" 
16. git log --author="john" 
17. git log --since="dd/mm/yyyy" 
18. git log --until="dd/mm/yyyy" 
19. git log --help 
20. git commit -am "msg" #add & commit functionality combined.Use this when file is tracked 
21. git commit --amend -m "msg"  #to add new msg to latest commit
22. git diff  #gives differene b/w working and stagging area 
23. git diff HEAD  #gives diff b/w working and local dir 
24. git restore --staged fileName  #to restore file in stagged area 
25. Undo of commits 
    1. Safe way 
        git revert 56asd89  #use SHA val for commit that u wants to revert. It add one more revert commit and if we revert that commit again we get original file one before this cmd excuted 
    2. Unsafe way 
        git reset --hard SHAVal  #move the head ptr to specified commit position. All above commits will lost 
        git reset --hard HEAD~2  #by use of head position 
26. Ignore (from being tracked) certain types of files like log, binary, exe files
    touch .gitignore 
    touch event.log 
    git status cat > event.log 
        some stuff inside this 
    open .gitignore and add event.log and save it 
    git status 
    #now all files name inside .gitignore will be ignores by git 
    #can be used to create a structure of project as empty folders are not seen by git, so add .gitignore(empty one) to those folders ***
27. git branch branchName  #to create a branch 
28. git checkout branchName  #to switch (HEAD) master to branchName 
29. git branch  #to know all branches 
30. git merge branchName  #to merge branchName to master first > git checkout master and then merge 
31. git switch branchName #same work as git checkout 
32. git branch -d branchName  #to delete a branch 
33. git log --graph --decorate --oneline  #to visualise the merging *** 
34. git rebase master #gives linear flow 
35. git branch -m oldBranchName newBranchName  #to rename a branch 
36. git checkout -b branchName SHAVal  #to recover a branch with SHAVal in > git log --oneline 
37. git tag tagName  #to tag recent commit 
38. git tag tagName SHAVal  #to tag commit wrt SHA val 
39. git tag -l patternToMatch  #display match pattern 
40. git stash  #to save tempo changes 
41. git stash list  
42. git stash apply  #to apply recent stored changes, and it's like stack where 0 index is the recent one 
43. git stash apply 1 
44. git stash save -m "msg here"
45. git stash pop  #pop the 0th index one ie. top-most *** 
46. git pull origin  #pull is combo for fetch and merge 
47. git push origin #origin is name of remote 
48. git push origin branch:branchName #to create a new branch in remote 
49. git checkout -b myBranchName origin/branchNameATRemote 
50. git fetch origin  #fetch the changes from remote to local repo not in working dir 
51. git rebase origin/main #rebase local main 
52. git remote -v 
53. git bundle create repo.bundle HEAD main  #to share the changes among peers when remote is under maintenance 
54. git clone repo.bundle repo