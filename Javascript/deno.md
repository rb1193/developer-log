# Deno

## The problems are the people behind Deno attempting to solve

1. Promises are native
2. The Node build system (gyp) was incredibly complex to use for package writers wanting to bind C libraries. This led to a lot of bugs when installing packages from NPM
3. The node_modules folder. Big and complex
4. The module system itself is kind of a bolt on, according to Ryan Dahl. Things like package.json and the index.js file, require without a file extension, have all become more complex than they should have
5. Security. The V8 engine behind node is totally sandboxed from the system it runs on by default, but Node opens connection to many system resources by default, meaning programs have much more access than they need to. There haven't been many (if any) exploits of this in the wild, but technically there is nothing stopping, for example, a linting program, from opening TCP connections or something. Deno allows users of a program to opt in to allow access to resources
6. Node is fast. It's really fast, but it can't reject requests, so under very heavy workloads the tail latency can be really bad. Deno can reject requests, allowing it to handle a consistent number of requests constantly
7. Include matching implementations of browser native APIs like fetch, where appropriate

## Talking points

1. Typescript native. But as TS is a superset of JS, JS can be used too, if we want
2. No package manager. Works by directly importing the requested file from a URL. It caches the code on build, the "--reload" flag can be used to re-download dependencies. The argument is that this is more like the web and therefore "better". You can also create an integrity-checked lockfile to make sure what you download in production matches exactly with what you are developing with
3. The standard libraries are largely ports of equivalent Go libraries, written in Typescript
4. Great tooling out of the box (some of this is a work in progress), including a linter, some basic testing assertions, a bundler and a documentation generator
5. Permissions. How much difference does this really make?
