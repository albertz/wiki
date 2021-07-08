# Backup software

Also see [backup hardware](backup-hardware.md).
Also see [personal knowledge base](personal-knowledge-base.md).

## My use case

### What I want to backup

There are overlaps between these points.
Also, temporary files might/should be excluded (e.g. `/tmp/*`).

* full Linux system including all files, such that recovering that will give me a fully functional system
* home directories
* archives (which are themselves backups of older computers/discs, where I don't have direct access to anymore)
* projects (programming but also other things) (usually Git repos)
* my pictures
* my music collection
* maybe movies (not so important)
* contact details (e.g. Google contacts)
* Tweets
* movie rankings (score11.de, imdb)
* documents / texts / mails


### Backup properties

* Certain files are more important than others (e.g. home directory files are quite important, programming projects, mails).
* I want to keep several copies around (on different media, PCs, online services).
  Not all copies must be complete, they could maybe just have the important files.
* Some overview where (media, PCs, online service) I have what backup, and which files are there, and maybe even the version of them.
* Some of the projects etc have their own versioning (e.g. Git repo).
  But this probably does not matter too much.
  Although it is not totally clear whether the backup system should have its own versioning support.
  It probably should not keep the full history of everything.
  Also it should be possible to permanently delete things from the whole system.
* Copying will take long, because of huge amounts of data. There has to be some continuous update.
* Backups on external cloud storage would be nice as well, but should be encrypted there.
* Some projects / pictures are published elsewhere (GitHub, Google Photos or so).
  It would be good if the system knows that. And maybe provides an easy way to publish further directories.


### File Index

In any case, I want to have an index of all the files,
and that index should contain meta information,
e.g. what backups contain the file, and other things.

The index could be part of the backup solution,
or external (but it should know about the multiple copies).

[Git-Annex](https://git-annex.branchable.com/) might be an option.

[Baloo](https://community.kde.org/Baloo) or others are maybe relevant for a search index.


## Software

* [Wikipedia software list](https://en.wikipedia.org/wiki/List_of_backup_software)
* [ArchLinux software list](https://wiki.archlinux.org/index.php/Synchronization_and_backup_programs)
* [Ubuntu software list](https://help.ubuntu.com/community/BackupYourSystem)
* [rsync](https://rsync.samba.org/)
* [duplicity](https://nongnu.org/duplicity/). Encrypted tar-format volumes, uploading them to a remote or local file server.
  No central index.
* [Bacula](https://bacula.org/)
* [Perkeep](https://perkeep.org/) (previously Camlistore).
  Also for indexing of pics, etc.
  Looks close to what I want.
  [Comparison](https://perkeep.org/doc/compare).
* [Upspin](https://upspin.io/)
  ([HN](https://news.ycombinator.com/item?id=13700492)).
  Similar to Perkeep, but different focus.
  Also very relevant.
* [Syncthing](https://syncthing.net/)
* [bup](https://bup.github.io/)
* [restic](https://restic.net/)
* [Box Backup](https://www.boxbackup.org/)
* [BorgBackup](https://www.borgbackup.org/)
  ([HN](https://news.ycombinator.com/item?id=21642364)).
  Used by rsync.net.
  Remotely encrypted backups.
  No central index.
* [Rclone](https://rclone.org/). "rsync for cloud storage".
  No central index of stored data.
* [BackupPC](https://backuppc.github.io/backuppc/)
* [Bareos](https://www.bareos.org/)
* [Areca Backup](http://www.areca-backup.org/)
* [Burp](https://burp.grke.org/)
* [git-annex](https://git-annex.branchable.com/)
* [Datalad](https://www.datalad.org/). On top of git-annex.
* [Dat](http://datproject.org)
* [Unison File Synchronizer](https://www.cis.upenn.edu/~bcpierce/unison/). project dead.
* [Seafile](https://github.com/haiwen/seafile)
* [albertz/backup_system](https://github.com/albertz/backup_system): incomplete
* [Resilio](https://www.resilio.com/individuals-sync/). commercial
* [Dropbox](https://www.dropbox.com/), [Google Drive](https://www.google.com/drive/), etc. commercial
* [imap-backup](https://github.com/joeyates/imap-backup)

A lot of the software can be divided into:

* Standard backup software:
  Choose what files to backup, and where.
  You are responsible for how many copies there are,
  and to keep track what files are backuped where.
  I.e. there is no global index of all files.
  They might be simpler to use, though.

* Global index based systems,
  like [Perkeep](https://perkeep.org/) or [Upspin](https://upspin.io/).
  They are not designed to work with lots of small files
  (e.g. Git object files, whole Linux systems, etc)
  but more for media files (images, documents).

The stored backup can have its own custom format
(e.g. for efficient incremental backups)
or it can be stored as-is.
A custom format means that accessing it needs custom tools,
might support custom FUSE, but is not as efficient.

It might make sense to decouple the storage of the files (maybe just as-is)
from the index (to keep track which backup or remote contains what files, etc).

Note that not all software seems to be maintained anymore.
Check the corresponding Git repo, whether it is still active.


## Related software

* [albertz/google-contacts-sync](https://github.com/albertz/google-contacts-sync): syncs Google contacts
* [albertz/memos](https://github.com/albertz/memos): collects Tweets. similar is [Timeliner](https://github.com/mholt/timeliner)
* [albertz/personal_assistant](https://github.com/albertz/personal_assistant): personal assistant. backup, or a knowledge base, is kind of an integrated part of this; or knowing where to find what data
* [albertz/system-tools](https://github.com/albertz/system-tools), [albertz/helpers](https://github.com/albertz/helpers): small tools to sync/download things, or create projects, etc
* [albertz/iphone-backup](https://github.com/albertz/iphone-backup)
* [Baloo](https://community.kde.org/Baloo) or others for indexing
* [Solid project](https://solidproject.org/),
  e.g. [Solid Google Takeout importer](https://github.com/solid/solid-takeout-import)


## [Perkeep](https://perkeep.org/)

What's missing from Perkeep for the outlined use case?
How would the workflow look like?

* The index of objects/files:
  - Is it easily synchronized, so always up-to-date?
  - Reasonable small enough, so every backup instance can have the full index?
    Or do we need partial index support?
  - Does it contain information on what media/PC we have the data?
    If not, can we add that?
    (I want to see, how many copies of some objects (or tree) are there,
     have control over that.)
* Good idea to just push all Git object files into it?
  - Should we then also push the checked out files into it?
    We already have all the data from the Git objects.
  - Can Perkeep directly read and understand the Git object files?
    Directly accessible (read-only) via FS?
* Would that work well with once-written/offline backup media (DVD, tape)?
* Automatic backup schedules:
  - Some trees (e.g. home dir) should automatically be synced to multiple online media.


## [Bup](https://bup.github.io/)

What's missing from Bup for the outlined use case?
How would the workflow look like?
Simpler than Perkeep (no concept of user, access control)
but that might not be a dealbreaker.

* Python 2?
* The index of objects/files:
  - Is it easily synchronized, so always up-to-date?
  - Index is a single file? Can it be distributed? Partial?
  - Does it contain information on what media/PC we have the data?
    If not, can we add that?


## [Git-Annex](https://git-annex.branchable.com/)

### Create multiple repos or one single?

If a single repo (maybe more convenient),
how would I link existing files into it?

### How to setup for existing files?

E.g. my current picture collections, which is already distributed, and partial in each copy.

Would I just go in one of the copies
and do `git init` and `git annex init`?

[Question in forum](https://git-annex.branchable.com/forum/Import_existing_files/)

### How to manage alternative keys

E.g. via local sensitive hashing (LSH).

[Question in forum](https://git-annex.branchable.com/forum/Fuzzy_local_sensitive_hashing___40__LSH__41__/)

### Difference to Datalad


## [Syncthing](http://syncthing.net)

### How good is the partial directory support?

Good also in the sense of how easy it is to use.
