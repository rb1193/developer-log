# Tools

## NPM / Yarn

When deploying sites using npm install, we should be using npm ci instead because the normal install command will upgrade packages if a newer version is available. Yarn has a similar option on its install command.

Yarn install may also change the lockfile for performance optimization reasons, potentially causing merge conflicts in production. The --frozen-lockfile option can be used to prevent this.

NPM can install global packages for your user on Unix systems by making use of the .local directory in your home folder, which exists specifically for this purpose. The way to tell NPM to install packages there is to use `npm config set prefix ~/.local` and then add `PATH=~/.local/bin/:$PATH’ to your .bashrc or profile

## Webpack

Webpack can “poll” for changes when watching code, which is useful when the code is on a shared file system, e.g. when running node inside vagrant
