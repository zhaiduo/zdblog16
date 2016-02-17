---
title: GAE提速方法总结
tags:
  - GoogleAppEngine
id: 1241
categories:
  - 网站技术
---

*   Compiled regular expressions.  All regular expressions are parsed and  stored in a compiled form.  You can store compiled regular expressions  in global variables, then use app caching to re-use the compiled objects  between requests.
*   [GqlQuery](http://code.google.com/appengine/docs/python/datastore/gqlqueryclass.html) objects.  The GQL query string is parsed when the GqlQuery object is  created.  Re-using a GqlQuery object with parameter binding and the [bind()](http://code.google.com/appengine/docs/python/datastore/gqlqueryclass.html#GqlQuery_bind) method is faster than re-constructing the object each time.  You can  store a GqlQuery object with parameter binding for the values in a  global variable, then re-use it by binding new parameter values for each  request.
*   Configuration and data files.  If your application loads and parses  configuration data from a file, it can retain the parsed data in memory  to avoid having to re-load the file with each request.
*   SELECT __key__ queries are faster and cost less CPU than SELECT * queries. Queries that return keys are faster and cost less CPU than queries that return entities, since the keys themselves are already in the index, so the query doesn't need to fetch the actual entities. If you only need the keys from your query results — for example, if you're just going to delete the results — consider using a keys only query.
*   You can batch put, get and delete operations for efficiency
*   Every entity for every App Engine app is stored in a singleBigTable  table! Further, when it comes to queries, all the queries that you can  execute natively (with the notable exception of those involving 'IN' and  '!=' operators - see above) have equivalent execution cost: The cost of  running a query is proportional to the number of results returned by  that query.
*   Requests to build new indexes are actually added to a queue of indexes  that need to be built, and processed by a centralized system that builds  indexes for all App Engine apps. At peak times, there may be other  index building jobs ahead of yours in the queue, delaying when we can  start building your index.
*   useGqlQuery .bind() to 'rebind' the values of the parameters for each  query. This is faster than constructing a new query each time, because  the query only has to be parsed once:
q = db.GqlQuery("SELECT * FROM People "
"WHERE first_name = :first_name "
"AND last_name = :last_name")
for first, last in people:
q.bind(first, last)
person = q.get()
print person
*   using re.compile() and saving the resulting regular expression object for reuse is more efficient when the expression will be used several times in a single program.