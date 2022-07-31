# Content addressable backup and sharing
We need to cover several scenarios, preferably within single system:
- data preservation:
	- redundant local storage
	- redundant remote storage / sync
- private sharing
- public sharing

Favorable system properties:
- mountable
- self-hosted
- decentralized
- content-addressable (automatic deduplication, cheap incremental backups)
- stable for years to come (data accessible thru more than single application)
- multiplatform
	- especially mobile client (autouploader)!

Possible software classes:
- backup
- distributed redundant FS

## [Ceph](https://ceph.com) (owned by Red Hat)
### Pro:
- redundant local and remote storage
- CephFS was merged into the Linux kernel in 2010
### Contra:
- not content-addressable
- no native access controll/sharing
- Ceph uses CRUSH hashing to automatically manage data placement, which is efficient to locate the data. But the data has to be placed according to the CRUSH algorithm. Any wrong configuration would cause data loss. Topology changes, such as adding new servers to increase capacity, will cause data migration with high IO cost to fit the CRUSH algorithm.

## [Keybase fs](https://book.keybase.io/docs/files/details) 
### Pro:
- simple global namespace, like '/keybase/public/writer1name,writer2name/' or '/keybase/private/writername#readername/'
- history
### Contra:
- service
- seems not content-addressable
## [Perkeep](https://perkeep.org/)
Self-hosted service, written in Go, listening on TCP port 3179
Write-only storage
### Pro:
- has Android autoupload App ready
- content-addressable
- written by Brad Fitzpatrik
### Contra:
- unclear sharing/access control mechanics (may be I have to just read more docs / try it)
- unclear support perspectives
- not focused on files
## [Upspin](https://upspin.io/)
### Pro:
- simple global namespace, like 'ann@example.com/dir/file'
- simple sharing. just put 'read: joe@here.com, moe@there.com' into file named 'Access' within folder to share the folder
### Contra:
- central key server
## [IPFS](https://ipfs.io https://github.com/ipfs/ipfs#quick-summary)
### Pro:
- has traction
- content addressable
- CDN gateways
### Contra:
- no private data
- mobile client is power hungry because of swarming
## [Kopia](https://kopia.io)
### Pro:
- End-to-End ‘Zero Knowledge’ Encryption
- local cache
- multiplatform
### Contra:
- backup only
- encryption is password-based
## [Git-annex](https://git-annex.branchable.com)
### Pro:
- git-based
### Contra:

Abandoned
- [Casync](https://github.com/systemd/casync)
- [cafs](https://github.com/indyjo/cafs)
- [sharebox-fs](https://github.com/chmduquesne/sharebox-fs)
- [DedupFS](https://github.com/xolox/dedupfs)
- [archivefs](https://github.com/tmbdev-archive/archivefs)
- [gpgfs](https://github.com/datapartyjs/gpgfs)
- [noms](https://github.com/attic-labs/noms/)
- [freehold](https://github.com/timshannon/freehold)(probably non content-addressable, just private file storage)

Promising:
- [Bup](https://bup.github.io/)
- [Tahoe-LAFS](https://tahoe-lafs.org/trac/tahoe-lafs) Decentralized cloud storage system. Distributes data across multiple servers
- [Borgbackup](https://www.borgbackup.org/)
- [Restic](https://restic.net)
- [libarchive](https://www.libarchive.org/)
- [storj](https://www.storj.io/)
- [dolt](https://github.com/dolthub/dolt) noms fork, drop-in MySQL replacement, but versioned

Used before:
- Unison
- Brackup
- Duplicity
- rsync
- Dropbox

Distributed file storage:
- [sia](https://sia.tech)
- [storj](https://www.storj.io/)
 - [skynet](https://skynetlabs.com)

Abandoned CAS projects:
- https://bazil.org/

See also
- [list of filesystems](https://en.wikipedia.org/wiki/List_of_file_systems)
- [git lfs](https://git-lfs.github.com)# Git extension for versioning large files
- [filestash](https://www.filestash.app)web frontend to several storage backends
- [freehold](https://github.com/timshannon/freehold)(probably non content-addressable, just private file storage)
- [garage](https://garagehq.deuxfleurs.fr)distributed s3 implementation
- [hdfs](https://www.bigdataschool.ru/wiki/hdfs)Hadoop Distributed File System (Open source GoogleFS clone)
- [glusterfs](https://www.gluster.org) (owned by Red Hat)
- [MinIO](https://min.io) FreeNAS и TrueNAS под капотом используют именно MinIO https://habr.com/ru/company/veeam/blog/517392/. Use several files per object - can hit inode limits
- [moosefs](https://moosefs.com) spinoff of Gemius internet analytics. Semi-opensource: "We have never aimed to create a developers community, although your ideas, bug reports and wishes are carefully taken into account by our developers"

Theory:
[f4: Facebook’s Warm BLOB Storage System](https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-muralidhar.pdf)
[Facebook’s Tectonic Filesystem: Efficiency from Exascale](https://www.usenix.org/system/files/fast21-pan.pdf)
