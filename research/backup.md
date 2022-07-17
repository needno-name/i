# Content addressable backup and sharing
We need to cover several scenarios, preferably within single system:
- redundant local storage
- redundant remote storage / sync
- private sharing
- public sharing

Favorable system properties:
- mountable
- self-hosted
- decentralized
- stable for years to come (data accessible thru more than single application)
- mobile client

## [Ceph](https://ceph.com)
### Pro:
- redundant storage
### Contra:
- not content-addressable
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
### Contra:
## [Git-annex](https://git-annex.branchable.com)
### Pro:
- git-based
- 
### Contra:
## [Casync](https://github.com/systemd/casync)
A combination of the rsync algorithm and content-addressable storage
### Pro:
- written by Lennart Poettering,
### Contra:
- abandoned