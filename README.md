# Nodelist-Inflator

This is a simple CLI tool to extract individual nodes (hostnames) from a nodelist and write them to a file to be used by DeepSpeed.

For example, if you have a nodelist containing the following:

```bash
ip-xxxxxx,ip-yyyyyy,ip-aaaaa-[b-c,f]
```

It will write the following to the file `hostname`

```bash
ip-xxxxxx slots=8
ip-yyyyyy slots=8
ip-aaaaab slots=8
ip-aaaaac slots=8
ip-aaaaaf slots=8
```

# Usage

Write a hostfile on the fly (useful for DeepSpeed integreations)
```console
foo@bar:~$ nodelist_inflate --nodelist=ip-xxxxxx,ip-yyyyyy,ip-aaaaa-[b-c,f] --write
```

Get the rank of the current host
```console
foo@bar:~$ nodelist_inflate --nodelist=ip-xxxxxx,ip-yyyyyy,ip-aaaaa-[b-c,f] --hostname=ip-xxxxxx
0 # the index of the hostname in the nodelist
``` 
