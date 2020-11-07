# Backup hardware

This complements with [backup software](backup-software.md).

For your backups
(and also any data in general,
 but see [backup software discussion about the type of data](backup-software.md))
you want to have some appropriate hardware.

That can include offline media, like tapes, DVDs etc
(or even hard drives which you archive).

Or it can be online / live, and then usually accessible via network in some way.
This is then called a [Network-attached storage (NAS)](https://en.wikipedia.org/wiki/Network-attached_storage) system
-- or at least, a NAS is very related.


## NAS

Never use hardware RAID but always software RAID.
ZFS scrub.

Some references:

* [Modular, extensible DIY NAS: Building the perfect, cheap DIY NAS, 2020](https://blog.georgovassilis.com/2020/04/01/building-the-perfect-cheap-diy-nas/).
  [HN discussion](https://news.ycombinator.com/item?id=24677407)
* [Installing FreeNAS on my QNAP TS-459, 2020](https://humaidq.ae/blog/qnap/) ([HN](https://news.ycombinator.com/item?id=23529147))


## Media

* Tape
  * [Linear Tape-Open (LTO), Wikipedia](https://en.wikipedia.org/wiki/Linear_Tape-Open)
  * [400 TB Storage Drives In Our Future: Fujifilm, 2020](https://www.anandtech.com/show/15888/400-tb-storage-drives-in-our-future-fujifilm)
  * LTO8: 100€ for 30TB, 30 years.

