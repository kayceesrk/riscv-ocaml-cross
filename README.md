# OCaml RISC-V cross compiler

Dockerfiles for OCaml RISC-V cross compilation.

Quick demo using pre-built image in Dockerhub.

```bash
$ docker run -it kayceesrk/riscv64-ocaml:0.1.0
root@45c50745d0f3:/# echo "let _ = print_int 42" > hello.ml
root@45c50745d0f3:/# ocamlopt hello.ml
root@45c50745d0f3:/# file a.out
a.out: ELF 64-bit LSB executable, UCB RISC-V, version 1 (SYSV), dynamically
linked, interpreter /lib/ld-linux-riscv64-lp64d.so.1, for GNU/Linux 3.0.0, with
debug_info, not stripped
```
