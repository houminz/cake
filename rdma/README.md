
# RDMA Programming Examples

## Compile

```bash
$ gcc -Wall -I/usr/local/ofed/include -O2 -o RDMA_RC_example -L/usr/local/ofed/lib64 -L/usr/local/ofed/lib -
 * libverbs RDMA_RC_example.c
```

## Run

```bash
# Server A
$ ./RDMA_RC_example

# Server B
$ ./RDMA_RC_example <ServerAIP>
```
