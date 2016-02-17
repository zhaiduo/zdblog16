---
title: Jquery要点
tags:
  - Jquery
id: 555
categories:
  - javascript
---

$(this).is('[type=checkbox],[type=radio]')
$('input[class='+name+']').each(function(){})
$(this).attr('name')
$(this).removeClass("select_hover");
$(this).addClass("select");
select = $(this).val();
jQuery.fn.custom = function(formid){};
$("div")..length;

1.4:
$("div:eq(0)").delay(5000);

$("#ban_site").change(function(){
$("#ban, #unban").attr('disabled',false);
site = $("#ban_site option:selected").text();
});
$("#ban").click(function(){
ajax_ban("#unban",0,user,site);
});

function ajax_roller(trg,i,max,is_lock,user){
	if(i <= max-1){
		var trg2=$(trg+" option:eq("+i+")");
		if(trg2){
			ajax_ban(trg,is_lock,user,trg2.text());
			trg2.delay(5000);
			i++;
			ajax_roller(trg,i,$(trg+" option").length,is_lock,user);
		}
	}
}