---
title: Selenium自动化测试
tags:
  - Selenium
  - 测试
  - 自动化测试
id: 2244
comment: false
categories:
  - 测试
---

selenium-webdriver
http://selenium.googlecode.com/git/docs/api/javascript/index.html

下载安装扩展组件：
Chrome	chromedriver(.exe)
http://chromedriver.storage.googleapis.com/index.html

Internet Explorer	IEDriverServer.exe
http://selenium-release.storage.googleapis.com/index.html

PhantomJS	phantomjs(.exe)
http://phantomjs.org/download.html

Opera	operadriver(.exe)
https://github.com/operasoftware/operachromiumdriver/releases

Safari	SafariDriver.safariextz
http://selenium-release.storage.googleapis.com/index.html

安装selenium-webdriver
cnpm install selenium-webdriver

//////////////////////////////////////
install the standalone server

Open a command prompt, navigate to the file location and enter the following command:

java -jar selenium-server-standalone-[version].jar

To run in IE, the command should be as follows:

java -jar selenium-server-standalone-[version].jar -Dbwebdriver.ie.driver=IEDriverServer.exe

写入bat，执行出错：Exception in thread "main" java.lang.NoClassDefFoundError
直接在命令行运行可以。java -jar selenium-server-standalone-2.45.0.jar

//////////////////////////////////////
https://www.npmjs.com/package/selenium-standalone
It will install a selenium-standalone command line that will be able to install selenium server and start firefox, chrome, internet explorer or phantomjs for your tests.

npm install selenium-standalone@latest -g
selenium-standalone install (dos下会下载失败，通过浏览器下载后，复制到C:\Program Files\nodejs\node_modules\selenium-standalone\.selenium\)
selenium-standalone start

//////////////////////////////////////////////
windows7下出错：node-gyp rebuild AttributeError: 'module' object has no attribute 'F_GETFD' gyp ERRor （可以忽略）

下载chromedriver_win32.zip等组件，解压chromedriver.exe到selenium目录，将selenium目录加入path。Mac下可编辑~./.bash_profile：
export PATH=/selenium/web:$PATH

然后运行 . .bash_profile
echo $PATH
看看是否有selenium目录
//////////////////////////////////////////////
windows7下调用IEDriver出错：UnknownError: Unexpected error launching Internet Explorer. Protected Mode setti
ngs are not the same for all zones. Enable Protected Mode must be set to the sam
e value (enabled or disabled) for all zones.

IE浏览器->internet安全选项->取消保护模式

///////////////////////////////////////////
windows7下调用IEDriver出错：
Unable to execute code, call to IHTMLWindow2::execScript failed

Windows Update KB3025390 for IE 11 Breaks IE Driver
http://jimevansmusic.blogspot.ru/2014/12/windows-update-kb3025390-for-ie-11.html
https://code.google.com/p/selenium/issues/detail?id=8302
所以暂时无法用IE11进行测试～
//////////////////////////////////////////////
Error: Could not locate Firefox on the current system

////////////////////////////////
centos7 64下node selenium.js 出错Error: spawn EACCES
把chromedriver chmod 755.

/////////////////////////////////
centos7 64下node selenium-server.js 出错:
The path to the driver executable must be set by the webdriver.chrome.driver system property.

办法
chmod 755 /chromedriver
java -jar selenium-server-standalone-2.35.0.jar -Dwebdriver.chrome.driver="./chromedriver"

/////////////////////////////////
centos7 64下node selenium-server.js 出错:
error while loading shared libraries: libgconf-2.so

原因：Linux based EC2 instances lack gtk+, which is a must to launch any GUI enabled applications. - See more at: http://itsallabtamil.blogspot.com/2013/02/setting-up-chrome-firefox-ec2-selenium-java.html#sthash.Ga4egJnu.dpuf

办法：yum install libgconf-2.so.4 -y
/////////////////////////////////
通过server网址访问出错：HTTP ERROR: 403 Forbidden for Proxy RequestURI=/session

var driver = new webdriver.Builder()
    //.forBrowser('firefox')
	.usingServer("http://localhost:4444")
	.withCapabilities(webdriver.Capabilities.chrome())
    .build();

办法：用这个路径 http://localhost:4444/wd/hub

http://localhost:4444/wd/hub/static/resource/hub.html
/////////////////////////////////////////////
node selenium.js出错：UnknownError: unknown error: Chrome failed to start: crashed
弹窗出错：“An administrator has installed Google Chrome on this system for all users. The installation of Google Chrome at system level will substitute the user level installation ”

An administrator has installed Google Chrome on this system, and it is available for all users. The system-level Google Chrome will replace your user-level installation now

** To get started with WebDriverJS for Node, you will need to download a copy of the ChromeDriver and ensure it can be found on your system PATH.

node selenium.js出错：UnknownError: chrome not reachable

直接使用系统安装的chrome [C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe]，无需使用下载的chromedriver.exe
////////////////////////////////////////////// Firefox
seleniumk-standalone start, node server.js
UnknownError: Cannot find firefox binary in PATH. Make sure firefox is installed

var firefox = require('selenium-webdriver/firefox');
var profile = new firefox.Profile();
profile.setPreference('extensions.firebug.showChromeErrors', true);

var options = new firefox.Options()
    .setProfile(profile)
    .setBinary('D:\\Program Files\\Mozilla Firefox\\firefox.exe');

var driver = new webdriver.Builder()
    .forBrowser('firefox')
    .usingServer('http://127.0.0.1:4444/wd/hub')
    .setFirefoxOptions(options)
    .build();

///////////////////////////////////////////
selenium server chrome出错：
Caused by java.io.IOException: Cannot run program "C:\P
rogram Files\nodejs\node_modules\selenium-standalone\.selenium\chromedriver\2.14
-x64-chromedriver

https://github.com/ariya/phantomjs/issues/12616
http://stackoverflow.com/questions/6674431/possible-causes-of-java-io-ioexception-createprocess-error-5
//////////////////////////////////////////////
最后node test.js
测试脚本：

`var webdriver = require('selenium-webdriver'),
    By = require('selenium-webdriver').By,
    until = require('selenium-webdriver').until;

var driver = new webdriver.Builder()
    .forBrowser('chrome')
    .build();

driver.get('https://www.baidu.com/');
driver.findElement(By.id('kw')).sendKeys('zhaiduo');
driver.findElement(By.id('su')).click();
driver.wait(until.titleIs('zhaiduo_百度搜索'), 3000);
driver.quit();`

运行后，chrome浏览器自动打开，并访问相应网址，自动执行脚本中的各种事件。

///////////////

语法参考：

driver.navigate("file:///race_condition.html")
el = driver.find_element_by_tag_name("p")
assert el.text == "Hello from JavaScript!"

def document_initialised(driver):
    return driver.execute_script("return initialised")

driver.navigate("file:///race_condition.html")
WebDriverWait(driver).until(document_initialised)
el = driver.find_element_by_tag_name("p")
assert el.text == "Hello from JavaScript!"

from selenium.webdriver.support.ui import WebDriverWait

driver.navigate("file:///race_condition.html")
el = WebDriverWait(driver).until(lambda d: return d.find_element_by_tag_name("p"))
assert el.text == "Hello from JavaScript!"

https://seleniumhq.github.io/docs/wd.html#driver_requirements

／／／／／／／／／练习

微博通过oauth自动登录，刷新微博

／／／／／／／／／扩展

可以做成自动化同步微博工具。
引用截屏插件

更多参考：
https://github.com/chibimagic/WebDriver-PHP

http://code.google.com/p/php-webdriver-bindings/