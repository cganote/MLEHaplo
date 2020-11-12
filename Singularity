Bootstrap: docker
From: ubuntu:14.04
Stage: spython-base

%files
Dockerfile /opt/
%labels
maintainer="li.weiling.1112@gmail.com"
author="raunaq.123@gmail.com"
%post
# install base packages
apt-get update && apt-get install -y wget git g++ make zlib1g-dev bc

# Install packages for perl scripts
apt-get install -y curl
curl -L https://cpanmin.us | perl - --sudo App::cpanminus
cpanm Graph
apt-get install -y libexpat1-dev
cpanm HTTP::Daemon
cpanm LWP::UserAgent
cpanm XML::Parser
cpanm Bio::SeqIO
cpanm Getopt::Long
cpanm --force Net::SSLeay
cpanm --force IO::Socket::SSL
cpanm LWP::Protocol::https
cpanm --force IO::Socket::IP
cpanm Bio::DB::GenBank
cpanm Bio::DB::GenPept
cpanm --force Bio::Perl

# Change workdir
cd /opt
git clone https://github.com/raunaq-m/MLEHaplo.git

# Install multi-dsk
cd /opt/MLEHaplo/multi-dsk
make k=64


cd /opt/MLEHaplo


%runscript
cd /opt/MLEHaplo
exec /bin/bash "$@"
%startscript
cd /opt/MLEHaplo
exec /bin/bash "$@"