---
title: 'Grunt Build Error: require.js blocks are no more supported'
tags:
  - Grunt
  - Yeoman
id: 2155
categories:
  - webapp
date: 2014-12-22 14:00:16
---

When I use Yo to test Backbone webapp, I get thie error:
`
Running "useminPrepare:html" (useminPrepare) task
Fatal error: require.js blocks are no more supported.
`
According to the discuss in [grunt-usemin](https://github.com/yeoman/grunt-usemin/issues/98), I update Gruntfile.js with requirejs.dis.options:

Insert the following options:
`
,
					include: '../bower_components/requirejs/require',
					mainConfigFile: yeomanConfig.app + '/scripts/main.js',
					out: yeomanConfig.dist + '/scripts/app.min.js'
`

Then update index.html in app category from
`
&lt;!-- build:js scripts/main.js --&gt;
        &lt;script data-main="scripts/main" src="bower_components/requirejs/require.js"&gt;&lt;/script&gt;
        &lt;!-- endbuild --&gt;
&lt;/code&gt;
to
<code>
&lt;!-- REMOVE THIS AFTER `grunt build` --&gt;
		&lt;script data-main="scripts/config" src="bower_components/requirejs/require.js"&gt;&lt;/script&gt;

		&lt;!-- UNCOMMENT THIS AFTER `grunt build` --&gt;
		&lt;!-- &lt;script src="scripts/app.min.js"&gt;&lt;/script&gt; --&gt;
`

The problem should be resolved.

And after build app to dist category, don't forget to change index.html, use app.min.js to replace requirejs/require.js.