---
title: Qunit测试用例
tags:
  - qunit
id: 2019
categories:
  - webapp
  - 单元测试
---

测试动作
function moveLeft(el, px, ms,callback) {
    el.animate({
        "left": px + "px"
    }, {
        duration: ms,
        complete:callback
    });
}
test("move 50", function () {
//      expect(2);   expect(2);
    var el = appendToTest();
    ok(el.css('left') == "auto", "element 0");
//define the calback function
      var callback = function(){equal(el.css("left"), "50px");start();}
//execute the test:
      stop();
       moveLeft(el, 50, 200,callback);
});

test("appendElement", function () {
    appendToTest()
    ok($("#wrapper").find('div'), "element appended");
})

function appendElement(el, to) {
    this.el = $("<" + el + "/>");
    $(to).append(this.el);
    return this.el;
}

function appendToTest() {
    return appendElement("div", "#wrapper");
}

测试位移

测试事件