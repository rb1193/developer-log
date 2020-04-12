# Git

It’s a good idea to tag git feature/release branches with an archive/{branch_name} tag before closing them, because once they’re closed they stay closed

To hide a file from git without adding it to the gitignore (e.g. when providing a dockerfile dev environment for an open source project you want to commit to), you can use the `.git/info/excludes` file
