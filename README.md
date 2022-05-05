# Kubernetes Config for PhpApp & Postgres with NFS.

Simpel project untuk konfigurasi kubernetes Phpapp & Postgres dengan NFS(Network File System).

## Langkah

- `apt install nfs-kernel-server nfs-common`

- Get NFS IP `wsl hostname -I`

## etc/exports

```linux
/srv/nfs/larapgsql/ *(rw,sync,no_subtree_check,insecure)
/srv/nfs/db_dataku/ *(rw,sync,no_root_squash,no_subtree_check,insecure)
```

- apply `exportfs -rav`
- reload 1 `sudo service rpcbind restart`
- reload 2 `sudo service nfs-kernel-server start`
- check `exportfs -v`

## Struktur Folder

```
  mkdir /srv/nfs/larapgsql/app -p
  sudo chown -R 82:82 .

  mkdir /srv/nfs/db_dataku/ -p
```
