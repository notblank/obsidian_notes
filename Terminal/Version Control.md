	Track changes to a collection of files and folders.

https://missing.csail.mit.edu/2020/version-control/

Changes stored in a series of snapshots + metadata (author, time, messages, etc)

Used to:
- look old version
- parallel work
- determining authoring and time of changes
- check when a test started failing (going back in time)


## Git Data Model

A snapshot:

```
root ( tree )
- dir1 ( tree )
	- file1 ( blob, contents = ... ) 
-file2 (blob, contents = ... )
```

Uses a DAG to model history. A snapshot is a node:

```
t0 <-  t1 <- now1 <--- future
	    ^--- now2 <-----|
```

Can have parallel branches.

Obs:
- Each snapshot contains metadata.

One possible implementation:

```
// a file is a bunch of bytes
type blob = array:byte

// a directory map from name to tree or blob 
type tree = map:string:(tree | blob)

// a commit has parents, metadata, and the top-level tree
type commit = struct {
    parents: array:commit
    author: string
    message: string
    snapshot: tree
}
```

All the above are unified as objects:

```
type object = blob | tree | commit
```

All objects are content addressed:

```
objects = string:object
```

object id = hash of object. So to store hash and set to id. To load use id.

### Objects and Refferences

Objects are identified by hash. 
Refferences have type name:object_id.

Obs:
- Refferences are mutable.
- The DAG cannot change.

### Some commands

```
git commit with hash 45eff
git log --all --graph --decorate   to see commit history
git checkout  move head pointer and changes dir content
git diff what's changed since some snapshot 
```


```
git checkout file_name --restores file to snapshot state
```

### Notation

- Head: Where are you looking
- Master: the latest commit (node)

### Branching and Merging

Base command:

```
git branch
```

Add:
- name -> creates name branch

Base command:

```
git merge
```

Conflicts:

resolve conflicts and continue with merge


## Remote Repos

```
git remote
```

- push/fetch to get/retreive from remote repo

```
git remote add remote_name remote_url
git push remote_name local_branch:remote_branch
git clone url folder_name
git fetch remote_name  get changes from remote
git pull = git fetch; git merge
```


## Other Functionalities

- git config --edit (~/.gitconfig)
- git clone --shallow (avoid cloning all commits. Use latest snapshot) 
- git add -p ( interactive add ) 
	- git diff --cached ( to see changes to commit )
- git blame ( who edited what in a file )
	- git show commit_hash ( to get more info ) 
- git stash ( put changes away temporarily )
	- git stash pop ( to undo )
- git bisect ( manually search history )
	- At what point did something broke?
	- give a unit test to see in which commit will it fail	
- .gitignore ( to ignore files )
	

