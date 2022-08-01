# Content addressable backup and sharing
We need to cover several scenarios, preferably within single system:
- data preservation:
	- redundant local storage
	- redundant remote storage / sync over slow and unreliable channel
- private sharing
- public sharing

Favorable system properties:
- self-hosted
- stable for years to come
- accessible thru more than single application, at least mountable
- multiplatform (especially mobile client/autouploader)
- relatively simple
- content-addressable (automatic deduplication, cheap incremental backups)
- asynchronous replication
- decentralized

Possible software types:
- backup
- distributed redundant FS

Used before:
- Unison
- Brackup
- Duplicity
- rsync
- Dropbox

- [Ceph](https://ceph.com) (owned by Red Hat)
Pro:
- redundant local and remote storage
- CephFS was merged into the Linux kernel in 2010
Contra:
- not content-addressable
- no native access controll/sharing
- [Ceph uses CRUSH hashing to automatically manage data placement, which is efficient to locate the data. But the data has to be placed according to the CRUSH algorithm. Any wrong configuration would cause data loss. Topology changes, such as adding new servers to increase capacity, will cause data migration with high IO cost to fit the CRUSH algorithm](https://github.com/seaweedfs/seaweedfs#compared-to-ceph).

[Keybase fs](https://book.keybase.io/docs/files/details) 
Pro:
- simple global namespace, like '/keybase/public/writer1name,writer2name/' or '/keybase/private/writername#readername/'
- history
Contra:
- service
- seems not content-addressable

[Perkeep](https://perkeep.org/)
Self-hosted service, written in Go
Write-only storage
Pro:
- has Android autoupload App ready
- content-addressable
- written by Brad Fitzpatrik
Contra:
- small traction - unclear future
- not focused on files

[Upspin](https://upspin.io/)
Pro:
- simple global namespace, like 'ann@example.com/dir/file'
- simple sharing. just put 'read: joe@here.com, moe@there.com' into file named 'Access' within folder to share the folder
Contra:
- central key server

[IPFS](https://ipfs.io https://github.com/ipfs/ipfs#quick-summary)
Pro:
- has traction
- content addressable
- CDN gateways
Contra:
- no private data
- mobile client is power hungry because of swarming

[Kopia](https://kopia.io)
Pro:
- End-to-End ‘Zero Knowledge’ Encryption
- local cache
- multiplatform
Contra:
- backup only
- encryption is password-based

[Git-annex](https://git-annex.branchable.com)
Pro:
- git-based
Contra:

Abandoned
- [casync](https://github.com/systemd/casync) written by Lennart Poettering
- [cafs](https://github.com/indyjo/cafs)
- [sharebox-fs](https://github.com/chmduquesne/sharebox-fs)
- [DedupFS](https://github.com/xolox/dedupfs)
- [archivefs](https://github.com/tmbdev-archive/archivefs)
- [gpgfs](https://github.com/datapartyjs/gpgfs)
- [noms](https://github.com/attic-labs/noms/)
- [bazil](https://bazil.org/)
- [freehold](https://github.com/timshannon/freehold)(probably non content-addressable, just private file storage)

Promising:
- [Bup](https://bup.github.io/)
- [Tahoe-LAFS](https://tahoe-lafs.org/trac/tahoe-lafs) Decentralized cloud storage system. Distributes data across multiple servers
- [Borgbackup](https://www.borgbackup.org/)
- [Restic](https://restic.net)
- [libarchive](https://www.libarchive.org/)
- [storj](https://www.storj.io/)
- [dolt](https://github.com/dolthub/dolt) noms fork, drop-in MySQL replacement, but versioned

Distributed file storage:
- [sia](https://sia.tech)
- [storj](https://www.storj.io/)
 - [skynet](https://skynetlabs.com)

See also
- [list of filesystems](https://en.wikipedia.org/wiki/List_of_file_systems)
- [git lfs](https://git-lfs.github.com)# Git extension for versioning large files
- [filestash](https://www.filestash.app)web frontend to several storage backends
- [freehold](https://github.com/timshannon/freehold)(probably non content-addressable, just private file storage)
- [garage](https://garagehq.deuxfleurs.fr)distributed s3 implementation
- [hdfs](https://www.bigdataschool.ru/wiki/hdfs)Hadoop Distributed File System (Open source GoogleFS clone)
- [glusterfs](https://www.gluster.org) (Red Hat) Provides replication, quotas, geo-replication, snapshots and bitrot detection
- [MinIO](https://min.io) FreeNAS & TrueNAS use MinIO https://habr.com/ru/company/veeam/blog/517392/ (ru). Use several files per object - problem of lots of small files (LOSF)
- [moosefs](https://moosefs.com) spinoff of Gemius internet analytics. Semi-opensource: "We have never aimed to create a developers community, although your ideas, bug reports and wishes are carefully taken into account by our developers"
- [zenko](https://www.zenko.io/) s3 implementation, support for multiple storage backends, full metadata search across all clouds, policy-based replication
- [seafile](https://www.seafile.com/)

Theory:
[Finding a needle in Haystack: Facebook’s photo storage](https://www.usenix.org/legacy/event/osdi10/tech/full_papers/Beaver.pdf)
[f4: Facebook’s Warm BLOB Storage System](https://www.usenix.org/system/files/conference/osdi14/osdi14-paper-muralidhar.pdf)
[Facebook’s Tectonic Filesystem: Efficiency from Exascale](https://www.usenix.org/system/files/fast21-pan.pdf)
[Erasure code](https://en.wikipedia.org/wiki/Erasure_code)