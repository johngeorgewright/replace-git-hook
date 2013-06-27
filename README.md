Replace
=======

This a server-side git hook that is used to overwrite another directory with what ever is pushed to it.

It will only allow tags (and branches if configured to do so) to be pushed. It can also be configured to disallow tag and branch modifications.

This is mainly used as a deployment script for simple websites/apps on remote servers.

Use
---

Symlink the files in to your bare server repo. This example assumes you have cloned `Replace` into a sibling directory called `replace-git-hook`.

```sh
# ~/my-project.git/hooks
ln -s ../replace-git-hook/update
ln -s ../replace-git-hook/post-receive
```

### Configuration options:

#### hooks.allowunannotated

This boolean sets whether unannotated tags will be allowed into the repository.  By default they won't be.

#### hooks.allowdeletetag

This boolean sets whether deleting tags will be allowed in the repository.  By default they won't be.

#### hooks.allowmodifytag

This boolean sets whether a tag may be modified after creation. By default it won't be.

#### hooks.allowdeletebranch

This boolean sets whether deleting branches will be allowed in the repository.  By default they won't be.

#### hooks.denycreatebranch

This boolean sets whether remotely creating branches will be denied in the repository.  By default this is allowed.

#### hooks.post-receive-replace.target

**Required full path** where your project lives. Ie: `/home/website/html`.

Without this configuration the hook will not take place.

#### hooks.post-receive-replace.source

A path relative to the source code which will be used to overwrite the project. `.` by default.

