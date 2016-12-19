---
layout: default
title: "Installing AWS on Laravel"
date: 2016-04-01
---


sudo yum -y install ImageMagic

sudo yum -y install libpng-devel libjpeg-devel libtiff-devel

yum install ImageMagick-devel

# Needed to enable swap
https://getcomposer.org/doc/articles/troubleshooting.md#proc-open-fork-failed-errors
/bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
/sbin/mkswap /var/swap.1
/sbin/swapon /var/swap.1
