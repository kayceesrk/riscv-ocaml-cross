# OCaml RISC-V cross compiler

Dockerfiles for OCaml RISC-V cross compilation.

Quick demo using pre-built image in Dockerhub.

```bash
$ docker run -it kayceesrk/riscv64-ocaml:0.1.0
root@933dfa3db228:~# echo 'let _ = print_endline "Hello,world!"' > hello.ml
root@933dfa3db228:~# ocamlopt -ccopt -static hello.ml
/riscv-ocaml/lib/ocaml/libasmrun.a(unix.o): In function `caml_dlopen':
/riscv-ocaml-src/asmrun/unix.c:276: warning: Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
root@933dfa3db228:~# file a.out
a.out: ELF 64-bit LSB executable, UCB RISC-V, version 1 (SYSV), statically linked, for GNU/Linux 3.0.0, with debug_info, not stripped
root@933dfa3db228:~# spike /usr/local/riscv64-unknown-elf/bin/pk ./a.out
Hello,world!
root@933dfa3db228:~#
```

## Acknowledgements

The riscv backend for OCaml is from the
[riscv-ocaml](https://github.com/nojb/riscv-ocaml) project. The
dockerfiles in this repo extend the dockerfile from
[riscv-tools-docker](https://github.com/anmolsahoo25/riscv-tools-docker), which
is a part of the [Shakti Processor Program](https://shakti.org.in/) at IIT
Madras.
