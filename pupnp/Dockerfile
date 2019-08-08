FROM fedora:27

RUN dnf install -y git wget make automake libtool

RUN wget https://master.dl.sourceforge.net/project/docpp/doc%2B%2B/3.4.10/doc%2B%2B-3.4.10-1.i386.rpm

RUN dnf install -y doc++-3.4.10-1.i386.rpm

RUN git clone https://github.com/mrjimenez/pupnp.git

WORKDIR pupnp

RUN ./bootstrap 
RUN ./configure 
RUN make html
