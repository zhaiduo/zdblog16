---
title: Apache绑定IPV6地址
tags:
  - Apache
  - IPV6
id: 1598
categories:
  - 杂项
---

IPv6 addresses must be specified in square brackets or the optional port number could not be determined. To enable Apache to listen to both stacks on separate sockets you will need to add a new “Listen” directive:
Listen [::]:80
Listen 0.0.0.0:80

And for your Virtual Hosts, the will look like this:
<virtualHost [2101:db8::a00:200f:fda7:00ea]>
ServerAdmin webmaster@yourdomain.com
DocumentRoot /www/docs/ipv6test.yourdomain.com
ServerName ipv6test.yourdomain.com
ErrorLog logs/ipv6test.yourdomain.com-error_log
TransferLog logs/ipv6test.yourdomain.com-access_log
<virtualHost>
4\. Add Addresses to DNS

The final step in getting up and running is to add your new IPv6 addresses to your DNS server. If you’re using a IPv6 enabled DNS server, you will simply insert an ‘AAAA’ resource record (aka quad-A record) for your host.
5\. Test Your Server’s IPv6 Accessibility

While your DNS is propagating, you can still test your webserver to see if it responds to the IP you assigned by using square brackets in your browser: http://[2101:db8::a00:200f:fda7:00ea]