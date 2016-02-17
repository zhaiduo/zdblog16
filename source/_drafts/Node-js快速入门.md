---
title: Node.js快速入门
tags:
  - Nodejs
id: 1578
categories:
  - javascript
  - 云时代
---

[Node.js基础](http://nodejs.org/api/index.html)
支持的文件类型：.js, .json, .node
运行程序：node example.js
获取程序名称：console.log(__filename);
当前目录：console.log(__dirname);
The core modules are defined in node's source in the lib/ folder.
获得参数：
process.argv.forEach(function (val, index, array) {
  console.log(index + ': ' + val);
});
切换目录：
console.log('Starting directory: ' + process.cwd());
try {
  process.chdir('/tmp');
  console.log('New directory: ' + process.cwd());
}
catch (err) {
  console.log('chdir: ' + err);
}
查看运行平台：console.log('This platform is ' + process.platform);
内存使用：
var util = require('util');
console.log(util.inspect(process.memoryUsage()));
并行运行：
process.nextTick(function () {
  console.log('nextTick callback');
});
检查nodejs运行时间：process.uptime()
查看数据内容：
var util = require('util');
console.log(util.inspect(util, true, null));
判断数组：util.isArray([])
满足匹配：util.isRegExp(/some regexp/)
util.isDate(new Date())
util.isError(new Error())
事件：require("events")
server.on('connection', function (stream) {
  console.log('someone connected!');
});
监听事件、取消监听：
var callback = function(stream) {
  console.log('someone connected!');
};
server.on('connection', callback);
// ...
server.removeListener('connection', callback);
监听端口：server.listen(port, [host], [callback])
设置最大连接数：server.maxConnections
异步删除：
var fs = require('fs');
fs.unlink('/tmp/hello', function (err) {
  if (err) throw err;
  console.log('successfully deleted /tmp/hello');
});
读文件：
fs.readFile('/etc/passwd', function (err, data) {
  if (err) throw err;
  console.log(data);
});
写文件：
fs.writeFile('message.txt', 'Hello Node', function (err) {
  if (err) throw err;
  console.log('It's saved!');
});
读文件信息：
fs.watchFile('message.text', function (curr, prev) {
  console.log('the current mtime is: ' + curr.mtime);
  console.log('the previous mtime was: ' + prev.mtime);
});
stats 《= fs.stat()
stats.isFile()
stats.isDirectory()
目录名：path.dirname('/foo/bar/baz/asdf/quux')
文件名：path.basename('/foo/bar/baz/asdf/quux.html')
是否存在：
path.exists('/etc/passwd', function (exists) {
  util.debug(exists ? "it's there" : "no passwd!");
});
建立TCP服务器：
var net = require('net');
var server = net.createServer(function(c) { //'connection' listener
  console.log('server connected');
  c.on('end', function() {
    console.log('server disconnected');
  });
  c.write('hellorn');
  c.pipe(c);
});
server.listen(8124, function() { //'listening' listener
  console.log('server bound');
});
建立TCP/UNIX服务器：
var server = net.createServer(function (socket) {
  socket.end("goodbyen");
});
// grab a random port.
server.listen(function() {
  address = server.address();
  console.log("opened server on %j", address);
});
解析域名：
var dns = require('dns');

dns.resolve4('www.google.com', function (err, addresses) {
  if (err) throw err;

  console.log('addresses: ' + JSON.stringify(addresses));

  addresses.forEach(function (a) {
    dns.reverse(a, function (err, domains) {
      if (err) {
        console.log('reverse for ' + a + ' failed: ' +
          err.message);
      } else {
        console.log('reverse for ' + a + ': ' +
          JSON.stringify(domains));
      }
    });
  });
});
HTTP服务器：http.createServer([requestListener])
node> require('url').parse('/status?name=ryan')
{ href: '/status?name=ryan',
  search: '?name=ryan',
  query: 'name=ryan',
  pathname: '/status' }
HTTP头返回：
var body = 'hello world';
response.writeHead(200, {
  'Content-Length': body.length,
  'Content-Type': 'text/plain' });
HTTP头状态：response.statusCode = 404;
写HTTP头状态：response.setHeader("Set-Cookie", ["type=ninja", "language=javascript"]);
返回内容：response.write(chunk, [encoding])
返回最后内容：response.end([data], [encoding])
HTTP POST/GET：http.request(options, callback)
var options = {
  host: 'www.google.com',
  port: 80,
  path: '/index.html'
};
获取返回内容：
request.on('response', function (response) {
  response.on('data', function (chunk) {
    console.log('BODY: ' + chunk);
  });
});
http.get(options, function(res) {
  console.log("Got response: " + res.statusCode);
}).on('error', function(e) {
  console.log("Got error: " + e.message);
});
SSL服务器：https.createServer(options, [requestListener])
生成Query参数串：querystring.stringify({ foo: 'bar', baz: ['qux', 'quux'], corge: '' })
解析Query参数串：querystring.parse('foo=bar&baz=qux&baz=quux&corge')
压缩/解压：
var zlib = require('zlib');
var gzip = zlib.createGzip();
var fs = require('fs');
var inp = fs.createReadStream('input.txt');
var out = fs.createWriteStream('input.txt.gz');

inp.pipe(gzip).pipe(out);
OS相关：
os.hostname()
os.type()
os.networkInterfaces()

[Express nodejs framework](http://expressjs.com/guide.html)
安装：npm install express
创建应用：express /tmp/foo && cd /tmp/foo
启动程序：node /tmp/foo/app.js
创建服务器：
var app = require('express').createServer();
app.get('/', function(req, res){
  res.send('hello world');
});
app.listen(3000);
服务器配置：
app.configure(function(){
    app.set('views', __dirname + '/views');
    app.set('views');
    // => "/absolute/path/to/views"

    app.enable('some feature');
    // same as app.set('some feature', true);

    app.disable('some feature');
    // same as app.set('some feature', false);

    app.enabled('some feature')
    // => false
 });
根据不同配置启动服务器：$ NODE_ENV=production node app.js
路径匹配：
app.get(/^/users?(?:/(d+)(?:..(d+))?)?/, function(req, res){
    res.send(req.params);
});
获取POST表单：
app.use(express.bodyParser());
app.post('/', function(req, res){
  res.send(req.body);
});
中间件(按顺序排列执行)：
var app = express.createServer(
      express.logger()
    , express.bodyParser()
  );
或使用configure() 配置：
app.use(express.logger({ format: ':method :url' }));
按顺序排列执行：
app.use(express.logger(...));
app.use(express.bodyParser(...));
app.use(express.methodOverride());
app.use(express.cookieParser());
app.use(express.session({ secret: "keyboard cat" }));
app.use(app.router);
app.use(express.static(...));
app.use(express.errorHandler({ showStack: true, dumpExceptions: true }));

错误处理：
function NotFound(msg){
  this.name = 'NotFound';
  Error.call(this, msg);
  Error.captureStackTrace(this, arguments.callee);
}

NotFound.prototype.__proto__ = Error.prototype;

app.get('/404', function(req, res){
  throw new NotFound;
});

app.get('/500', function(req, res){
  throw new Error('keyboard cat!');
});
监听错误：
app.error(function(err, req, res, next){
    if (err instanceof NotFound) {
        res.render('404.jade');
    } else {
        next(err);
    }
});
模板渲染：
app.set('view engine', 'jade');
app.set('view options', {
  layout: false
});
app.enable('view cache');
app.get('/', function(req, res){
    res.render('index.jade', { title: 'My Site', layout: 'mylayout' });
});
判断类型：
req.is('json');
是否是图片：
 app.is('an image', function(req){
      return 0 == req.headers['content-type'].indexOf('image');
    });
    Checks route params (req.params), ex: /user/:id
    Checks query string params (req.query), ex: ?id=12
    Checks urlencoded body params (req.body), ex: id=12
HTTP头：
res.header('Content-Length', 123);
res.charset = 'ISO-8859-1';
res.attachment('path/to/my/image.png');
res.sendfile(path, function(err){
  if (err) {
    next(err);
  } else {
    console.log('transferred %s', path);
  }
});
设置buffer:
res.sendfile(path, { bufferSize: 1024 }, function(err){
  // handle
});
下载：
res.download('path/to/image.png','name', function(err){
  // handle
});
相当于：
res.attachment(file);
res.sendfile(file);
错误检测：
res.download(path, function(err){
  // error or finished
}, function(err){
  // connection related error
});
返回状态码：
res.send(404);
返回json：
res.json({ user: 'tj' });
跳转：
res.redirect('/', 301);
cookie设置：
res.cookie('rememberme', 'yes', { expires: new Date(Date.now() + 900000), httpOnly: true });
res.cookie('rememberme', 'yes', { maxAge: 900000 });
获取cookie:
app.use(express.cookieParser());

app.get('/', function(req, res){
  // use req.cookies.rememberme
});
删除cookie:
res.clearCookie('rememberme');