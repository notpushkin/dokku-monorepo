dokku-monorepo
===============

Dokku plugin for monorepo setups.

## Install

```
dokku plugin:install https://gitlab.com/iamale/dokku-monorepo
```

## Usage

```
$ ls
.dokku-monorepo
myapp1
myapp2
```

The file .dokku-monorepo contains paths for applications to be deployed:
```
first=myapp1
second=myapp2/backend
```

The part before `=` is used to identify the dokku application. For example, here:
```
$ git remote -v
first             dokku@dokku.me:example-first
first-staging     dokku@dokku.me:example-first-staging
second            dokku@dokku.me:example-second
```

the `example-first` and `example-staging-first` applications would be deployed from the `myapp1` folder.

When you push the code to an application's remote, the folder gets detected for you:
```
$ git push first
Counting objects: 253, done.
Writing objects: 100% (253/253), 38.27 KiB | 0 bytes/s, done.
Total 253 (delta 117), reused 233 (delta 109)
=====> Monorepo detected
=====> Installing from ./myapp1
-----> Cleaning up...
-----> Building example-first from herokuish...
-----> Adding BUILD_ENV to build environment...
-----> Python app detected
       ...
```

It's that easy!
