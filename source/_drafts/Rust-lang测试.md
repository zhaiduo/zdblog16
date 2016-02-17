---
title: Rust-lang测试
tags:
  - rust
id: 2131
categories:
  - Coding
---

[Rust](http://www.rust-lang.org/)是一种性能接近C的高性能并发，类型、内存安全的的开发语言。

centos7安装：$ curl -s https://static.rust-lang.org/rustup.sh | sudo sh
或者直接： wget tar.gz包，解压，运行./install.sh即可

cargo new hello_rust --bin
cd hello_rust

如果cargo run --verbose出错，说没有librustc_driver.so，可以这样：
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:"/usr/local/lib"

emacs src/main.rs

C+x, 然后C+c退出