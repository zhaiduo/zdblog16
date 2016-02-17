---
title: VPS管理日记
tags:
  - VPS
id: 1514
categories:
  - Linux/Unix
---

**SSHD重启问题：cat: /proc/sys/crypto/fips_enabled: No such file or directory**

ok, what i did was looked at other sshd files on other servers similar to this one and looked at that line and saw that none of them had that weird file lookup string. So i took that whole if statement from the other sshd file and replaced it and now the sshd starts just fine with no warnings or anything.

I replaced this:

  if [ ! -s $RSA1_KEY -a cat /proc/sys/crypto/fips_enabled -eq 0 ]; then
     echo -n $"Generating SSH1 RSA host key: "
        rm -f $RSA1_KEY
        if $KEYGEN -q -t rsa1 -f $RSA1_KEY -C '' -N '' >&/dev/null; then
            chmod 600 $RSA1_KEY
            chmod 644 $RSA1_KEY.pub
            if [ -x /sbin/restorecon ]; then
               /sbin/restorecon $RSA1_KEY.pub
         fi
         success $"RSA1 key generation"
           echo
       else
           failure $"RSA1 key generation"
           echo
           exit 1
     fi
 fi
}

with this

  if [ ! -s $RSA1_KEY ]; then
        echo -n $"Generating SSH1 RSA host key: "
        rm -f $RSA1_KEY
        if $KEYGEN -q -t rsa1 -f $RSA1_KEY -C '' -N '' >&/dev/null; then
            chmod 600 $RSA1_KEY
            chmod 644 $RSA1_KEY.pub
            if [ -x /sbin/restorecon ]; then
               /sbin/restorecon $RSA1_KEY.pub
         fi
         success $"RSA1 key generation"
           echo
       else
           failure $"RSA1 key generation"
           echo
           exit 1
     fi
 fi
}

按照上面修改后，错误确实没有了，不过service sshd restart并没有换到新的端口。

**iptables restart出错**
“iptables” is due to our paravirt kernel having a “security” chain compiled into it, and the default “iptables” init script included with CentOS does not know how to handle it. Resolve this issue by downloading an amended version of the “iptables” init script.
cd /etc/init.d
mv iptables ~/iptables.bak
wget http://epoxie.net/14867.txt && cat 14867.txt | tr -d 'r' > iptables
chmod +x iptables
rm -rf 14867.txt