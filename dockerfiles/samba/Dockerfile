FROM ubuntu:18.04

ARG DEBIAN_FRONTEND=noninteractive

RUN DEBIAN_FRONTEND=noninteractive apt update \
    && DEBIAN_FRONTEND=noninteractive apt upgrade -y
RUN DEBIAN_FRONTEND=noninteractive apt install samba -y

RUN mkdir /SHARE \
    && chmod 0777 /SHARE

RUN adduser --system samba \
    # && passwd samba < "samba" \
    && (echo "samba"; echo "samba";) | smbpasswd -s -a samba

EXPOSE 137/udp 138/udp 139 445

ENTRYPOINT ["/usr/sbin/smbd", "-F", "-S"]