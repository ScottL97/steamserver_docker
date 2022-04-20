FROM centos

COPY run_dedicated_servers.sh /home/steam/run_dedicated_servers.sh

# 之后去root权限，用steam用户操作
#RUN useradd -m steam && \
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-* && \
    sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-* && \
    yum update -y && yum clean all && yum makecache && yum install -y wget glibc.i686 zlib.i686 libstdc++.i686 unzip && \
    ln -s /usr/lib64/libcurl.so.4 /usr/lib64/libcurl-gnutls.so.4 && \
    mkdir -p /home/steam/.klei/DoNotStarveTogether && \
# chown -R steam:steam /home/steam/.klei && \
    mkdir /home/steam/steamcmd && mkdir /home/steam/dst && \
    cd /home/steam/steamcmd && wget http://media.steampowered.com/installer/steamcmd_linux.tar.gz && \
    tar -xzf steamcmd_linux.tar.gz && \
# ./steamcmd.sh +force_install_dir /home/steam/dst +login anonymous +app_update 343050 validate +quit && \
    cd /home/steam && \
# wget https://accounts.klei.com/assets/gamesetup/linux/run_dedicated_servers.sh && \
    chmod 750 run_dedicated_servers.sh && \
    sed -i 's/\$HOME/\/home\/steam/g' run_dedicated_servers.sh

ENTRYPOINT /home/steam/run_dedicated_servers.sh
