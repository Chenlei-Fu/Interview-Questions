# Git
### Git push
1. Copy the local commits that are not existed in the remote repo to the remote repo
2. Move the origin/master (both in your local git and in the remote git) to point to the same local/master commit
3. Push DOES NOT merge


### Git pull
1. a fetch, i.e. all the extra commits from the server are copied into the local repo and the origin/master branch pointer moves to the end of the commit chain

2. a merge of the origin/master branch into the master branch, the master branch pointer moving to the newly created commit, while the origin/master pointer staying put.