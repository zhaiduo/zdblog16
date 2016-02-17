---
title: Jquery对Select的操作说明
tags:
  - Jquery
id: 628
categories:
  - javascript
date: 2010-06-09 17:30:11
---

最近要用到Jquery对Select的操作，总结一下，以备参考：

*   获取Select长度: $("#select option").length、所选长度：$("#select option:selected").length or size()
*   取得序号
$("#select option").index($("#select option:selected"))
*   获取Option显示的文字：$("#select option:eq("+i+")").text() - i是option的序号
*   获取Option的value：$("#select option:eq("+i+")").val() 或者attr("value")
*   清除所有Option：$("#select").html("");
*   删除Option
$("#select option:eq("+i+")").replaceWith(""); - i是option的序号
$("#select option:eq("+i+")").remove();
*   改变选择的Option
$('#select option:selected').removeAttr('selected');
$('#select option[value='+i+']').attr('selected','selected');
*   增加Option
$("&lt;option value='"+value+"'&gt;"+name+"&lt;/option&gt;").appendTo("#select");
*   通过value选定Option
*   $("#select").val("zhaiduo").attr("selected", "selected");