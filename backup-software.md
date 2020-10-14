# Backup software

Also see [backup hardware](backup-hardware.md).

## My use case

### What I want to backup

There are overlaps between these points.
Also, temporary files might/should be excluded (e.g. `/tmp/*`).

* full Linux system including all files, such that recovering that will give me a fully functional system
* home directories
* archives (which are themselves backups of older computers/discs, where I don't have direct access to anymore)
* projects (programming but also other things)
* my pictures
* my music collection
* maybe movies (not so important)
* contact details (e.g. Google contacts)
* Tweets
* movie rankings (score11.de, imdb)
* documents / texts / mails


### Backup properties

* Certain files are more important than others (e.g. home directory files are quite important, programming projects, mails).
* I want to keep several copies around. Not all copy must be complete, they could maybe just have the important files.
* Some overview where I have what backup, and which files are there, and maybe even the version of them, would be useful.
* Some of the projects etc have their own versioning (e.g. Git repo). But this probably does not matter too much. Although it is not totally clear whether the backup system should have its own versioning support. It probably should not keep the full history of everything. Also it should be possible to permanently delete things from the whole system.
* Copying will take long, because of huge amounts of data. There has to be some continuous update.
* Backups on external cloud storage would be nice as well, but should be encrypted there.
* Some projects / pictures are published elsewhere (GitHub, Google Photos or so). It would be good if the system knows that. And maybe provides an easy way to publish further directories.


## Software

* [Wikipedia software list](https://en.wikipedia.org/wiki/List_of_backup_software)
* [ArchLinux software list](https://wiki.archlinux.org/index.php/Synchronization_and_backup_programs)
* [Ubuntu software list](https://help.ubuntu.com/community/BackupYourSystem)
* [rsync](https://rsync.samba.org/)
* [duplicity](https://nongnu.org/duplicity/)
* [Bacula](https://bacula.org/)
* [Perkeep](https://perkeep.org/): previously Camlistore.
    Also for indexing of pics, etc.
    Looks close to what I want.
* [Syncthing](https://syncthing.net/)
* [bup](https://bup.github.io/)
* [restic](https://restic.net/)
* [Box Backup](https://www.boxbackup.org/)
* [BorgBackup](https://www.borgbackup.org/)
  ([HN](https://news.ycombinator.com/item?id=21642364)).
  Used by rsync.net.
  Remotely encrypted backups.
* [Rclone](https://rclone.org/)
* [BackupPC](https://backuppc.github.io/backuppc/)
* [Bareos](https://www.bareos.org/)
* [Areca Backup](http://www.areca-backup.org/)
* [Burp](https://burp.grke.org/)
* [albertz/backup_system](https://github.com/albertz/backup_system): incomplete
* [Resilio](https://www.resilio.com/individuals-sync/). commercial
* [Dropbox](https://www.dropbox.com/), [Google Drive](https://www.google.com/drive/), etc. commercial


## Related software

* [albertz/google-contacts-sync](https://github.com/albertz/google-contacts-sync): syncs Google contacts
* [albertz/memos](https://github.com/albertz/memos): collects Tweets. similar is [Timeliner](https://github.com/mholt/timeliner)
* [albertz/personal_assistant](https://github.com/albertz/personal_assistant): personal assistant. backup, or a knowledge base, is kind of an integrated part of this; or knowing where to find what data
* [albertz/system-tools](https://github.com/albertz/system-tools), [albertz/helpers](https://github.com/albertz/helpers): small tools to sync/download things, or create projects, etc
* [albertz/iphone-backup](https://github.com/albertz/iphone-backup)
