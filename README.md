# Composer template for ADM Distribution
This distribution is based on Drupal 9.

## Usage

To create a project based on ADM Distribution:

```
composer create-project adminteractive/adm-project:9.x-dev some-dir --stability dev --no-interaction
```

The `composer create-project` command passes ownership of all files to the 
project that is created. You should create a new git repository, and commit 
all files not excluded by the .gitignore file.

## Updating Drupal Core

Follow the steps below to update your core files.

1. Run `composer update drupal/core --with-dependencies` to update Drupal Core and its dependencies.
1. Run `git diff` to determine if any of the scaffolding files have changed. 
   Review the files for any changes and restore any customizations to 
  `.htaccess` or `robots.txt`.
1. Commit everything all together in a single commit, so `web` will remain in
   sync with the `core` when checking out branches or running `git bisect`.
1. In the event that there are non-trivial conflicts in step 2, you may wish 
   to perform these steps on a branch, and use `git merge` to combine the 
   updated core files with your customized files. This facilitates the use 
   of a [three-way merge tool such as kdiff3](http://www.gitshah.com/2010/12/how-to-setup-kdiff-as-diff-tool-for-git.html). This setup is not necessary if your changes are simple; 
   keeping all of your modifications at the beginning or end of the file is a 
   good strategy to keep merges easy.

## Common problems

**Update failed (The .git directory is missing from [path], see https://getcomposer.org/commit-deps for more information)**

This is normal when the dependency is installed through git (.git directories are removed by default; dev dependencies usually come through git).
Composer should offer an option to reinstall the package, so just agree with that.

**Cannot apply patch [patch]!**

The patch is already applied or the code have changed. 
You should look into the related issue. Issue number is always in patch url (it usually includes the comment number also).