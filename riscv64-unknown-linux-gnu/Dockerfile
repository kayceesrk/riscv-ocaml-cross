FROM iitmshakti/riscv-dev:0.5.0 as riscv-ocaml-cross
RUN apt-get -y update
RUN git clone https://github.com/kayceesrk/riscv-ocaml -b 4.07+cross riscv-ocaml-src
WORKDIR riscv-ocaml-src
RUN ./configure -no-ocamldoc -no-debugger -prefix /riscv-ocaml && \
    make -j8 world.opt && make install
ENV PATH="/riscv-ocaml/bin:${PATH}"
RUN make clean && \
		./configure --target riscv64-unknown-linux-gnu -prefix /riscv-ocaml \
		-no-ocamldoc -no-debugger -target-bindir /riscv-ocaml/bin && \
		make -j4 world || /bin/true
RUN make -j4 opt
RUN cp /riscv-ocaml/bin/ocamlrun byterun
RUN make install

FROM iitmshakti/riscv-dev:0.5.0
RUN apt-get -y update
ENV PATH="${PATH}:/riscv-ocaml/bin"
COPY --from=riscv-ocaml-cross /riscv-ocaml /riscv-ocaml

ENTRYPOINT ["/bin/bash"]
