# Git

It’s a good idea to tag git feature/release branches with an archive/{branch_name} tag before closing them, because once they’re closed they stay closed

To hide a file from git without adding it to the gitignore (e.g. when providing a dockerfile dev environment for an open source project you want to commit to), you can use the `.git/info/exclude` file

When using package managers, if writing an application, commit the lock file and use an install command such as `npm ci` or `composer install` to install the exact set of requirements from the lockfile during development and deployment. When writing a library, there is significant debate but the majority opinion seems to be not to commit the lockfile.
