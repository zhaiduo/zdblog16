---
title: 接触RSA算法
id: 200
categories:
  - PHP
date: 2007-08-16 01:17:48
tags:
---

前两天刚看了[RSA生成公匙和私匙的文章](http://zh.wikipedia.org/wiki/RSA%E5%8A%A0%E5%AF%86%E6%BC%94%E7%AE%97%E6%B3%95)，没想到今天就有机会亲自去试试。

主要原理就是：<span class="style1">利用</span>RSA算法<span class="style1">生成公钥和私钥两个字符串，分别保存在两个文件中，</span><span class="style1">公钥是公开的，供其他人加密数据使用，而私钥是属于私人保管的用于解密</span><span class="style1">数据</span><span class="style1">。</span>

RSA - 非对称加密演算法主要功能包括：
> 创建密钥
> 按指定密钥长度初始化密钥(32位-2048位)
> 计算e,d,n值，生成密钥对(公钥和私钥)
> **n为两素数(q,p)之积: n=p*q
> 取任一数e,要求满足e<(p-1)*(q-1)并且e与(p-1)*(q-1)互素（就是最大公因数为1）
> 从而计算d*e%t==1
> n d两个数就构成公钥；
> n e两个数就构成私钥**
> 获取保存公钥
> 获取保存私钥
> 
> 用公钥加密数据
> 导入需要加密的数据
> 导入公钥
> 利用公钥中e和n。对于m计算密文的公式是m的e次方再与n求模。
> 获取数据的大整数
> 加密数据
> 保存加密后数据
> 
> 用私钥对加密数据解密
> 读取加密数据
> 导入私钥
> 取得私钥的参数d,n
> 解密数据
RSA的缺点在于计算速度慢，另外如果大数n越容易被分解，就越容易被破解，推荐密钥长度最少1024位。

关于用PHP来实现RSA，我主要参考了[PEAR](http://pear.php.net/manual/en/)上的[Crypt_RSA模块](http://pear.php.net/package/Crypt_RSA)，另外遇到的问题在于大整数十进制和十六进制的转换，[php.net](http://www.php.net) 也有不少解决方案。

[code lang="php"]
function mydec2hex($number){
$hexvalues = array('0','1','2','3','4','5','6','7','8','9','A','B','C','D','E','F');
$hexval = '';
while($number != '0'){
$hexval = $hexvalues[bcmod($number,'16')].$hexval;
$number = bcdiv($number,'16',0);
}
return $hexval;
}
[/code]

总的来说，感觉对RSA有了初步的认识，希望能够做些更深入的学习。

补充：关于同余(congruence)的概念

若 <span class="MATH">_n_</span> 是某个正整数，<span class="MATH">_m_<sub>1</sub></span>与 <span class="MATH">_m_<sub>2</sub></span> 是整数，如果 <span class="MATH">_n_</span> 可以整除 <span class="MATH">_m_<sub>1</sub> - _m_<sub>2</sub></span> ， 那么：<span class="MATH">_m_<sub>1</sub></span> 与 <span class="MATH">_m_<sub>2</sub></span>， 在模 <span class="MATH">_n_</span> 之下同余 (<span class="MATH">_m_<sub>_i_</sub></span> is congruent to <span class="MATH">_m_<sub>2</sub></span> modulo <span class="MATH">_n_</span>)， 记为：![tongyu.gif](http://www.zhaiduo.com/wp-content/data/tongyu.gif) <span class="MATH" />