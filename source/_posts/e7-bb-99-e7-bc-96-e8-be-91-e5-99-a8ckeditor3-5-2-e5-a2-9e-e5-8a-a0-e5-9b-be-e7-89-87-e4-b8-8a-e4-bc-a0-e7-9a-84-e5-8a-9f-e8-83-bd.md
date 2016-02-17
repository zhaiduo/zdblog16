---
title: 给编辑器CKEditor3.5.2增加图片上传的功能
tags:
  - Ajax
  - CKEditor
  - 编辑器
id: 1307
categories:
  - PHP
date: 2011-03-07 01:13:46
---

[CKEditor](http://ckeditor.com/)是一款很适合PHP后台系统使用的HTML编辑器，功能强大，配置方便。唯独不足是缺少对图片上传的支持。CKFinder虽然是个解决方案，但是太过复杂，CKEditor的版本已经发展到3.5.2，网上很多解决办法还没更上，3.5.2的解决办法不太好找。考虑到ckeditor的复杂性，觉得用[valums的ajax upload](http://valums.com/ajax-upload/)来配合最合适。

首先在ckeditor的pluginsimagedialodsimage.js里进行编辑，找到
children:[{id:'txtUrl',type:'text',label:b.lang.common.url
在后面增加内容变成：
b.lang.common.url+" &lt;div id="file-uploader" style="display:inline;"&gt;上传图片&lt;/div&gt;"

然后在编辑器所在页面增加：
&lt;script src="fileuploader.js" type="text/javascript"&gt;&lt;/script&gt;
&lt;link href="fileuploader.css" rel="stylesheet" type="text/css" /&gt;
&lt;script&gt;
function createUploader(){
var uploader = new qq.FileUploader({
element: document.getElementById('file-uploader'),
action: 'ajax_upload.php',
debug: false
});
}
&lt;/script&gt;

最后修改fileuploader.js，找到：

var item = this._getItemByFileId(id);
qq.remove(this._find(item, 'cancel'));
qq.remove(this._find(item, 'spinner'));
if (result.success){

将后面的内容替换成：

if (result.success){

if(document.getElementById('cke_109_textInput')){
document.getElementById('cke_109_textInput').value=result.img;
}

}

注意cke_109_textInput是源文件图片路径框的ID号。

[![](http://www.zhaiduo.com/wp-content/uploads/2011/03/20110307005845.jpg "20110307005845")](http://www.zhaiduo.com/wp-content/uploads/2011/03/20110307005845.jpg)