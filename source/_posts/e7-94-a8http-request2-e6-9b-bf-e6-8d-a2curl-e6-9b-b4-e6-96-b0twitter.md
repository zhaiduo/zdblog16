---
title: 用HTTP_Request2替换Curl更新Twitter
tags:
  - 更新
id: 462
categories:
  - PHP
date: 2010-01-08 11:57:12
---

由于更换服务器，不再支持[Curl模块](http://www.php.net/manual/en/ref.curl.php)。所以决定使用Pear的[HTTP_Request2](http://pear.php.net/manual/en/package.http.http-request2.intro.php)包来更新更新Twitter。

原Curl代码:
> $ch = curl_init($url);
>         if($postargs !== false){
>             curl_setopt ($ch, CURLOPT_POST, true);
>             curl_setopt ($ch, CURLOPT_POSTFIELDS, $postargs);
>         }
>         if($this->username !== false && $this->password !== false)
>             curl_setopt($ch, CURLOPT_USERPWD, $this->username.':'.$this->password);
>         curl_setopt($ch, CURLOPT_VERBOSE, 1);
>         curl_setopt($ch, CURLOPT_NOBODY, 0);
>         curl_setopt($ch, CURLOPT_HEADER, 0);
>         curl_setopt($ch, CURLOPT_USERAGENT, $this->user_agent);
>         curl_setopt($ch, CURLOPT_FOLLOWLOCATION,1);
>         curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
>         curl_setopt($ch, CURLOPT_HTTPHEADER, $this->headers);
>         $response = curl_exec($ch);
>         $this->responseInfo=curl_getinfo($ch);
>         curl_close($ch);
>         if(intval($this->responseInfo['http_code'])==200){
>             if(class_exists('SimpleXMLElement')){
>                 $xml = new SimpleXMLElement($response);
>                 return $xml;
>             }else{
>                 return $response;
>             }
>         }else{
>             return false;
>         }

换为Pear::HTTP_Request2：
> $req = new HTTP_Request2($url, HTTP_Request2::METHOD_GET);
>     		$req->setHeader($this->headers);
>     		if($postargs !== false){
> 	    		$arr_post=explode("&",$postargs);
> 	    		for($i=0,$imax=count($arr_post);$i<$imax;$i++){
> 	    			$item_arr=explode("=",$arr_post[$i]);
> 	        	$req->addPostParameter($item_arr[0], $item_arr[1]);
> 	        }
>         }
>         $req->setBody('');
>     	$response = $req->send()->getBody();
>     	if (200 == $req->send()->getStatus()) {
>                 return $response;
>         }else{
>                  return false;
>         }

下载解压HTTP_Request2来相同目录，如需测试，还需要下载[Net_URL2](http://pear.php.net/package/Net_URL2)和[PHPUnit](http://www.phpunit.de/)。运行AllTests.php显示如下：
> PHPUnit 3.4.6 by Sebastian Bergmann.
> 
> .................................
> 
> Time: 0 seconds, Memory: 5.00Mb
> 
> OK (33 tests, 80 assertions)
表示安装HTTP_Request2正确。