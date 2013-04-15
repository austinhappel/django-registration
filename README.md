# Django user registration

This is a fork of the Django-registration module written by [ubernostrum](https://bitbucket.org/ubernostrum) found [here](https://bitbucket.org/ubernostrum/django-registration).

## Modifications I've made:

* **REGISTRATION_DEFAULT_USER_NAME** [(commit)](https://github.com/austinhappel/django-registration/commit/53e5de780d059c5f506ba2f8b792ba4c6b80b94e): If you want all of your newly registered users to be in a specific group by default, add this variable to your settings file.

## Notes on the branches

* **master** is the lastest *stable* release from the original mercurial repository, with any modifications, listed above, applied.
* **upstream** is the raw, latest work from the original repository - no changes made.
* **develop** is where I'm making in-progress changes/tweaks, most likely merging in the latest commits from the upstream branch.

# Installation using pip

General example:

    pip install git+git://github.com/austinhappel/django-registration.git@<tag, branch, or commit SHA>

For most likely a stable install:

    pip install git+git://github.com/austinhappel/django-registration.git@master

For bleeding edge:
    
    pip install git+git://github.com/austinhappel/django-registration.git@develop


# Creating the merged git/hg repository

I'm not sure if this will work on other's machines, but it's worth documenting. Because this is a hybrid mercurial/git repo, you need to do a lot of tricky stuff to get it working correctly.

1. Install [git-hg](https://github.com/cosmin/git-hg)
2. Clone the mercurial repo using git-hg
    
        git-hg clone ssh://hg@bitbucket.org/ubernostrum/django-registration

3. This should get all the history from the original mercurial repo and convert it to a git repository.
4. Add the remote to my repository:

        git remote add origin git@github.com:austinhappel/django-registration.git

5. Rename **master** branch to **upstream**

        git branch -m master upstream

6. Fetch everything from my repo:

        git fetch origin

7. Create orphan **master** and **develop** branches, then pull them down from my repository.

        git checkout --orphan master
        git pull origin master

        git checkout --orphan develop
        git pull origin develop

8. Set the upstream branch to track the mercurial master branch:

        git config hg.tracking.upstream "master"

If you did everything right, your upstream branch should be identical to, or a fast-forward version of my upstream branch. When you run `git pull origin upstream` you should get something to the tune of "everything is up-do-date" or "your version is ahead of origin". The master and develop branches should have parity with my repository.

Now you can pull the latest code from the original mercurial repository using:

    git checkout upstream
    git-hg pull



========================
Django user registration
========================

This is a fairly simple user-registration application for Django,
designed to make allowing user signups as painless as possible. It
requires a functional installation of Django 1.3 or newer, but has no
other dependencies.

For installation instructions, see the file "INSTALL" in this
directory; for instructions on how to use this application, and on
what it provides, see the file "quickstart.rst" in the "docs/"
directory.