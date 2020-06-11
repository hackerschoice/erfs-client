# thc-rfs-client
Encrypted Remote File System CLIENT

This tool allows one or multiple users to mount and share a remote encrypted filesystem. The server is provided by THC as a courtesy (free, as in free beer!). The data is not accessible to us. Only the user with the knowledge of the SHARE-SECRET can access the data.

It is possible to mount the filesystem from multiple computers at the same time. The data is securely and seamlessly syncronized. The server has no knowledge of the content and can not access to the data. All key material is created on the user's computer and never stored or transfered to the server.

Features:  
- Does not require root or superuser priviledges
- Server has no access to the data
- FileSystem can be mounted from multiple computers at the same time.
- Multi-User support
- 256 bit AES encryption

Currently supported OS:  
- Linux  
- MacOS  

It is possible to create, mount and share multiple different filesystems. There is no limit per user (for now). 

By using our server ("the service") you agree that you will only use the service for research or for doing good things. You agree you will not use the service for illegal activities. If in doubt then please run your own server.

---
**Pre-Requisite**
```
$ apt-get update -y
$ apt-get install -y git sshfs encfs
```

**Installation**
```
$ git clone https://github.com/hackerschoice/thc-rfs-client.git
$ export PATH=$PATH:${PWD}/thc-rfs-client
```

**Use**

Create a SHARE-SECRET and initialize a new File Share:
```
$ thc-rfs init
```

Mount the Remote File Share on your computer:
```
$ thc-rfs mount <SHARE-SECRET> ~/secure
```

The server does not have access to the SHARE-SECRET or the data. Keep the SHARE-SECRET secure. Anyone with the knowledge of the SHARE-SECRET can access the data.

---
Unmount everything:
```
$ thc-rfs umount <SHARE-SECRET>
```

---
**Sharing**

If you receive a SHARE-SECRET then you can access somebody's else secure share and collaborate at the same time. 
```
$ 
$ thc-rfs mount <SHARE-SECRET>
```

---
**Security**

Passing the SHARE-SECRET by command line parameter is insecure. A better way is:
```
$ export BLAH=<SHARE-SECRET>
$ ./thc-rfs mount /dev/stdin <<<"${BLAH}"
$ unset BLAH
```

The tools relies on the security of ssh, sshfs and EncFS.

---
**Running your own sever**

You can run your own server if you desire to do so. This is optional. Please refer to [hackerschoice/docker-thc-rfs-server](https://github.com/hackerschoice/docker-thc-rfs-server) for more information.
