---
title: yii框架快速入门
id: 1893
categories:
  - 杂项
tags:
---

Layouts
<?php echo $content; ?>
This is a magic line as it pulls in the page-specific content. If the site you’re looking at now used Yii, the value of $content would be all the HTML that makes up this post you’re reading.

自定义layout
public function actionAbout() {
    $this->layout = 'somewhere';
    $this->render('about');
}

指定sub路径
# protected/controllers/SiteController.php
public function actions() {
    return array(
        'page' => array('class' => 'CViewAction')
    );
}

# protected/controllers/SomeController.php
public function actionAbout() {
    $this->render('about');
}

http://www.example.com/index.php?r=site/page&view=about or,
http://www.example.com/index.php/site/page/view/about,

指定静态路径
# protected/controllers/SiteController.php
public function actions() {
    return array(
        'page' => array(
            'class' => 'CViewAction',
            'basePath' => 'static'
        )
    );
}

/site/page/view/company.board would display the protected/views/site/pages/company/board.php page

By default, if no $_GET['view'] value is provided, CViewAction will attempt to display an index.php static file.
# protected/controllers/SiteController.php
public function actions() {
    return array(
        'page' => array(
            'class' => 'CViewAction',
            'defaultView' => 'about' //index as default
        )
    );
}

其他页调用$content
<!--?php $this--->beginContent('//directory/file.php'); ?>
// Content.
<!--?php $this--->endContent(); ?>

======Model Events
afterConstruct()
afterDelete()
afterFind()
afterSave()
afterValidate()
beforeDelete()
beforeFind()
beforeSave()
beforeValidate()

The CComponent class provides three main tools:

The ability to get and set attributes
Event handling
Behaviors

# protected/models/SomeModel.php
protected function afterSave() {
    // Do relation Model method()
    return parent::afterSave();
}

# protected/models/Page.php
protected function beforeValidate() {
    if(empty($this->user_id)) { // Set to current user:
        $this->user_id = Yii::app()->user->id;
    }
    return parent::beforeValidate();
}

# protected/models/AnyModel.php::rules()
array('date_entered', 'default', 'value'=>new CDbExpression('NOW()'), 'on'=>'insert'),
array('date_updated', 'default', 'value'=>new CDbExpression('NOW()'), 'on'=>'update'),

or

# protected/models/AnyModel.php
public function beforeSave() {
    if ($this->isNewRecord) {
        $this->created = new CDbExpression('NOW()');
    } else {
        $this->modified = new CDbExpression('NOW()');
    }
    return parent::beforeSave();
}

These are the default rules set in the configuration file:

'rules'=>array(
    '<controller:w+>/<id:d+>' => '/view',
    '<controller:w+>/<action:w+>/<id:d+>' => '/',
    '<controller:w+>/<action:w+>' => '/',
),

So page/42 is associated with the route “page/view”.
# protected/controllers/PageController.php
public function actionView($id) {
    // Etc.
}

# protected/config/main.php
'verify/<x:d+>/<y:w+>' => 'user/verify',
# protected/controllers/UserController.php
public function actionVerify($x, $y) {
    // Etc.
    }

Case Sensitivity
the regular expression w+ will match Post, post, or pOsT, only post will match a controller in your application.

Routes

$this->createUrl('') returns the URL for the current page.
# protected/controllers/PageController.php
public function actionDummy() {
    $url = $this->createUrl('user/index'); // user/index
}
$url = $this->createUrl('view', array('id' => 42)); // page/view id=42
$url = Yii::app()->createUrl('page/view', array('id' => 42));
The main difference between the two versions of the createUrl() method is that the CController version can be used without referencing a controller ID, whereas the Yii::app() version (i.e., that defined in CApplication) requires a controller ID be provided.

Cookies
 Yii::app()->request->cookies array
 Yii::app()->session

Yii::app()->request->cookies['name'] = new CHttpCookie('name', 'value');
Yii::app()->request->cookies['name']->value
To test if a cookie exists, just use isset() on Yii::app()->request->cookies['name'],
Delete: unset(Yii::app()->request->cookies['name']);
Yii::app()->request->cookies->clear();

$cookie = new CHttpCookie('name', 'value');
Then adjust the expire attribute:

$cookie->expire = time() + (60*60*24); // 24 hours
Then add the cookie to the application:

Yii::app()->request->cookies['name'] = $cookie;

You can also improve the security of your cookies by setting Yii’s enableCookieValidation to true, in the Yii configuration file:

return array(
    'components'=>array(
        'request'=>array(
            'enableCookieValidation'=>true,
        ),
    ),
);

To prevent a CSRF attack on your site, first make sure that all significant form submissions use POST instead of GET. You should be using POST for any form that changes server content anyway, but a CSRF POST attack is a bit harder to pull off than a GET attack.

Second, set enableCsrfValidation to true in your configuration file:

return array(
    'components'=>array(
        'request'=>array(
            'enableCsrfValidation'=>true,
        ),
    ),
);

Sessions
 you don’t have to invoke session_start()

Yii::app()->session['var'] = 'value';
echo Yii::app()->session['var']; // Prints "value"
unset(Yii::app()->session['var']);

Within that, you would add a “session” element to the “components” array, wherein you customize how the sessions behave. The key attributes are:

autoStart, which defaults to true (i.e., always start sessions)
cookieMode, with acceptable values of none, allow, and only, equating to: don’t use cookies, use cookies if possible, and only use cookies; defaults to allow
cookieParams, for adjusting the session cookie’s arguments, such as its lifetime, path, domain, and HTTPS-only
gCProbability, for setting the probability of garbage collection being performance, with a default of 1, as in a 1% chance
savePath, for setting the directory on the server used as the session directory, with a default of /tmp
sessionName, for setting the session’s, um, name, which defaults to PHPSESSID
timeout, for setting after how many seconds a session is considered idle, which defaults to 1440

protected/config/main.php:

'session' => array (
    'autoStart' => false,
),

If you are using sessions, for security purposes, you may want to change the session’s name, always require cookies, and change the save path:

'session' => array (
    'sessionName' => 'Site Access',
    'cookieMode' => 'only',
    'savePath' => '/path/to/new/directory',
),

 For this reason, changing the save path to a directory within your own site can be a security improvement. Alternatively, you can store the session data in a database. To do that, add this code to the “components” section of protected/config/main.php:

'session' => array (
    'class' => 'system.web.CDbHttpSession',
    'connectionID' => 'db',
    'sessionTableName' => 'actual_table_name',
),

Yii::app()->session->sessionID.

 To do so, call Yii::app()->session->clear() to remove all of the session variables. Then call Yii::app()->session->destroy() to get rid of the actual data stored on the server.

Rendering

public function actionUpdate($id) {
    $data=$this->loadModel($id);

    $this->render('update',array(
        'model'=>$data
    ));
}
The render() method takes an optional third argument, which is a Boolean indicating if the rendered result should be returned to the Controller instead of sent to the Web browser

<?php echo $this->renderPartial('_form', array('model'=>$model)); ?>

Then indicate the subdirectory and file, still omitting the extension:

<?php echo $this->renderPartial('//search/_form'); ?>

Forms

<?php $form = $this->beginWidget('CActiveForm', array(
    'id'=>'user-form',
    'enableAjaxValidation'=>true,
    'focus'=>array($model,'firstName'),
)); ?>

<?php $this->endWidget(); ?>

Validation scenarios

Now when you wish to run validation under a specific scenario you must define it in when calling CModel::validate(), as so

<?php

//in user model
public function rules() {
	return array(
		//Set required fields
 		//Applies to 'register' scenario
 		//Note 'on' property
		array('username, password, password_repeat, email', 'required', 'on' => 'register'),

		//Applies to 'recover' scenario
		array('email', 'required', 'on' => 'recover'),

		//Applies to all scenarios
		array('username, password', 'length', 'max'=>35, 'min'=>3),

		//This rule checks if the username is unique in the database in
		//the 'register' scenario (we don't want it to check for uniqueness
		//on the login page for instance)
		array('username', 'unique', 'on' => 'register'),

		//This rule applies to 'register' and 'update' scenarios
		//Compares 'password' field to 'password_repeat' to make sure they are the same
		array('password', 'compare', 'on' => 'register, update'),
	);
}

$user->validate('<scenarioName>'); //runs validation under the given scenario

//example:
if ($user->validate('register')) {
	$user->save(false);
}

Console Application

 Related Models
 a foreign key (FK)

// protected/models/Posts
public function relations() {
    return array(
        'categories' => array(self::HAS_MANY, 'Categories', 'postId')
    );
}

Now Posts has a categories attribute, meaning that the following form code will work.

<div>
<?php echo $form->labelEx($model,'categories'); ?>
<?php echo $form->dropDownList($model, 'categories', CHtml::listData(
Categories::model()->findAll(), 'id', 'category'), array('multiple'=>'multiple', 'size'=>5)
); ?>
<?php echo $form->error($model,'categories'); ?>
</div>
 when you create a relation, that relation becomes an attribute of the Model.

public function actionCreate() {
    $model=new Posts;
    if(isset($_POST['Posts'])) {
        $model->attributes=$_POST['Posts'];
        if($model->save()) {
            foreach ($_POST['Posts']['categories'] as $categoryId) {
                $postCategory = new PostsCategories;
                $postCategory->postId = $model->id;
                $postCategory->categoryId = $categoryId;
                if (!$postCategory->save()) print_r($postCategory->errors);
            }
Now, when a new Post is created, one new record is created in PostsCategories for each selected category.

This method is called for the update, delete, and view actions and just returns a single Model. The Model is loaded using:

$this->_model=Posts::model()->findbyPk($_GET['id']);

After that, within the loadModel() method, you can add this code to fetch the associated PostsCategories:

$criteria=new CDbCriteria;
$criteria->condition='postId=:postId';
$criteria->select = 'categoryId';
$criteria->params=array(':postId'=>$_GET['id']);
$postCategories = PostsCategories::model()->findAll($criteria);

That code selects all of the categoryId values from PostsCategories where the postId value equals this post’s id. Next, we need to turn those results into an array:

$categories = array();
foreach ($postCategories as $category) {
    $categories[] = $category->categoryId;
}
Now, $categories is an array of numeric values, one for each category associated with the post. Just add this to the loaded Model:

$this->_model->categories = $categories;

 The easiest way to handle all possibilities is to clear out the existing values (for this post) in the PostsCategories table, and then add them in anew. To do that, in actionUpdate() of the PostsController, you would have:

if($model->save()) {
    $criteria=new CDbCriteria;
    $criteria->condition='postId=:postId';
    $criteria->params=array(':postId'=>$model->id);
    PostsCategories::model()->deleteAll($criteria);

Handling Checkboxe

<?php echo $form->checkBox($model,'attribute',array('value' => 'Y', 'uncheckValue'=>'N')); ?>

Forcing Login

'behaviors' => array(
    'onBeginRequest' => array(
        'class' => 'application.components.RequireLogin'
    )
),
Next, create a file called RequireLogin.php and store it in the protected/components directory. That file needs to define the RequireLogin class
<?php
class RequireLogin extends CBehavior
{
	public function attach($owner)
	{
	    $owner->attachEventHandler('onBeginRequest', array($this, 'handleBeginRequest'));
	}
	public function handleBeginRequest($event)
	{
	    if (Yii::app()->user->isGuest && !in_array($_GET['r'],array('site/login'))) {
		Yii::app()->user->loginRequired();
	    }
	}
	//when the onBeginRequest event occurs, this class’s handleBeginRequest() method should be called.

	public function handleBeginRequest($event)
	{
	    if (Yii::app()->user->isGuest && !in_array($_GET['r'],array('site/login'))) {
		Yii::app()->user->loginRequired();
	    }
	}

}
?>

MemCached
'cache' => array (
    'class' => 'CMemCache',
    'servers'=>array(
        array(
            'host'=>'localhost',
            'port'=>11211,
        ),
    ),
),

 Access Control

 a Controller’s accessRules() method dictates who can do what. In a very simple way, the “what” refers to the Controller’s action methods, like actionList() or actionDelete().

 represented by * (anyone) and @ (logged-in users),
public function accessRules()
{
    return array(
        array('allow',  // allow all users to perform 'list' and 'show' actions
            'actions'=>array('list','show'),
            'users'=>array('*'),
        ),
        array('allow', // allow authenticated user to perform 'create' and 'update' actions
            'actions'=>array('create','update'),
            'users'=>array('@'),
        ),
        array('allow', // allow admin user to perform 'admin' and 'delete' actions
            'actions'=>array('admin','delete'),
            'users'=>array('admin'),
        ),
        array('deny',  // deny all users
            'users'=>array('*'),
        ),
    );
}

Perhaps your users in the database would be registered by user type, or role, and that the permissions would be based upon these roles. In that case, you can add an expression element to the returned array in the access rules:

array('allow',
    'actions'=>array('admin','delete'),
    'users'=>array('@'),
    'expression'=>'PHP code to be evaluated'
),

array('allow',
    'actions'=>array('publish'),
    'users'=>array('@'),
    'expression'=>'isset($user->role) && ($user->role==="editor")'
),

public function actionDelete()
{
    $event = $this->loadEvents(); // Fetch the specific event Model.
    // Can only delete the events they created:
    if ($event->ownerId == Yii::app()->user->id) {
        $event->delete();
    } else {
        throw new CHttpException(403,'Invalid request. You are not allowed to delete this event.');
    }
}

Custom Authentication
 In this post, I want to change that behavior so that:

Authentication is performed against a database table
The user’s email address is used instead of their username
The user’s ID is stored for later reference
The user’s “role” is stored for later reference

'user'=>array(
    // enable cookie-based authentication
    'allowAutoLogin'=>true,
),
To disable cookie-based authentication, either remove that code entirely, or change allowAutoLogin to false.

ome/PHP/Configuring FCKEditor for Yii-Driven Sites

Configuring FCKEditor

To use the FCKEditor in a form, you’ll need to edit the _form.php file for the particular View. For example, on one site I edited protected/views/page/_form.php, as the admin created the site’s content through a Page Model. By default the form will have a standard textarea for every TEXT type MySQL column:

<?php echo CHtml::activeTextArea($model,'content',array('rows'=>6, 'cols'=>50)); ?>
To use FCKEditor instead of the textarea, invoke the integration widget by replacing that code with this:

<?php $this->widget('application.extensions.fckeditor.FCKEditorWidget',array(
 'model'     =>  $model,
 'attribute' => 'content',
 'height'    =>  '600px',
 'width'     =>  '100%',
 'fckeditor' =>  dirname(Yii::app()->basePath).'/htdocs/fckeditor/fckeditor.php',
 'fckBasePath' => Yii::app()->baseUrl.'/fckeditor/')
 ); ?>

open fckeditor/editor/filemanager/connectors/php/config.php in your text editor or IDE.
session_start();
$Config['Enabled'] = (isset($_COOKIE['PHPSESSID']) && (in_array('moderator', $_SESSION))) ;

A logical work-around is to use PHP’s strip_tags() instead, providing it with the optional second argument of allowable tags:

echo strip_tags($model->content, '

<a><div><ul><ol><li><span>');

Integrating Zend_Lucence

 The result will be a folder named ZendFramework-x.y.z. (where x.y.z represent the full version number). Within that folder, go into library/Zend and copy Exception.php to protected/vendors/Zend.
so you’ll want to include it while developing and debugging Zend_Lucene with Yii. Also copy the Search folder to protected/vendors/Zend.
class SearchController extends CController
{
    private $_indexFiles = '../runtime/search';
    public function actionIndex() {}
    public function actionCreate() {}
    public function actionSearch() {}
    public function actionUpdate() {}
}

Within three of the methods (not actionIndex()), the Controller will use Zend_Lucene. In order to do so, this script needs access to the Zend files, so import the contents of the vendors directory at the top of this script, just before the class definition begins:

Yii::import('application.vendors.*');

Then, include the Lucene.php page, found within the Zend Framework Search folder:

require_once('Zend/Search/Lucene.php');

Now this Yii Controller can create objects of type Zend_Search_Lucene, which is defined in that file. The actions will use that object type to perform the searches. To start, the index action just renders the index View:

public function actionIndex()
{
    $this->render('index');
}

public function actionCreate() {
    $index = new Zend_Search_Lucene($this->_indexFile, true);
    // Add documents to the database.
    $index->commit();
    $this->render('create');
}

 you could add a single HTML page to the search database by doing this:

$url = 'http://www.example.com/index.php/page/show/id/1';
$doc = Zend_Search_Lucene_Document_Html::loadHTMLFile($url);
$index->addDocument($doc);

Lastly, there’s the search action. This action would check for search terms, run the search against the database, then send the results on to a View:

public function actionSearch() {
    if (isset($_GET['terms'])) {
        $index = new Zend_Search_Lucene($this->_indexFile);
        $results = $index->find($_GET['terms']);
        $this->render('search', array('results' => $results));
    } else {
        $this->render('index');
    }
}

## Search Results for "<?php echo CHtml::encode($_GET['terms']); ?>"

<?php if ($results): ?>
    <?php foreach($results as $result): ?>
        <p><?php echo CHtml::encode($result->title); ?>

    <?php endeach; ?>
<?php else: ?>

No results matched your search terms.

<?php endif; ?>

Using CDbCriteria

$criteria = new CDbCriteria();

condition	The WHERE clause
limit	The LIMIT value
offset	The offset value in a LIMIT clause
order	The ORDER BY clause
params	The variables to be bound to the parameters
select	The columns to be selected

$criteria = new CDbCriteria();
$criteria->condition = 'id=:id';
$criteria->params = array(':id'=>$id);
$model = Page::model()->find($criteria);

or

$model = Page::model()->find(array(
    'condition' => 'id=:id',
    'params' => array(':id'=>$id)
));

// Find the number of "live" pages:
$criteria = new CDbCriteria();
$criteria->condition = 'live=1';
$count = Page::model()->count($criteria);
 equivalent to running a SELECT COUNT(*) FROM page WHERE live=1

$criteria = new CDbCriteria();
$criteria->condition = 'email=:email';
$criteria->params = array(':email'=>$email);
if (User::model()->exists($criteria)) {
    $message = 'That email address has already been registered.';
} else {
    $message = 'That email address is available.';
}

    $criteria = new CDbCriteria;
//函数方式
    $criteria->addCondition("id=1"); //查询条件，即where id = 1
    $criteria->addInCondition('id', array(1,2,3,4,5)); //代表where id IN (1,23,,4,5,);
    $criteria->addNotInCondition('id', array(1,2,3,4,5));//与上面正好相法，是NOT IN
    $criteria->addCondition('id=1','OR');//这是OR条件，多个条件的时候，该条件是OR而非AND
    $criteria->addSearchCondition('name', '分类');//搜索条件，其实代表了。。where name like '%分类%'
    $criteria->addBetweenCondition('id', 1, 4);//between 1 and 4

    $criteria->compare('id', 1);    //这个方法比较特殊，他会根据你的参数自动处理成addCondition或者addInCondition，
                                    //即如果第二个参数是数组就会调用addInCondition

    $criteria->addCondition("id = :id");
    $criteria->params[':id']=1;

//属性方式
    $criteria->select = 'id,parentid,name'; //代表了要查询的字段，默认select='*';
    $criteria->join = 'xxx'; //连接表
    $criteria->with = 'xxx'; //调用relations
    $criteria->limit = 10;    //取1条数据，如果小于0，则不作处理
    $criteria->offset = 1;   //两条合并起来，则表示 limit 10 offset 1,或者代表了。limit 1,10
    $criteria->order = 'xxx DESC,XXX ASC' ;//排序条件
    $criteria->group = 'group 条件';
    $criteria->having = 'having 条件 ';
    $criteria->distinct = FALSE; //是否唯一查询

$criteria = new CDbCriteria();
$criteria->select = 'table_name,model_id,sum(amount) total';
$criteria->group = 'table_name,model_id';
$criteria->addCondition("$nIdcId=4");//也可以$criteria->condition = "$nIdcId=4";
$aResult = accessory_info::model()->findAll($criteria);

$c = new CDbCriteria();
$c->select = 't.id, t.created_at, t.outsource_id, t.user_id, t.operate, t.content';
$c->join = 'LEFT JOIN outsource ON outsource.id=t.outsource_id';
$c->condition = 'outsource.idc_id IN(' . implode(',', $idc_ids)  . ')';

if($last_log_id) {
    $c->condition .= " AND t.id > $last_log_id";
}

$c->limit = 20;
$c->order = 't.id DESC';

$logs = OutsourceProcessLog::model()->findAll($c);

//可见
$c = new CDbCriteria();
$c->join = "JOIN idc_user on t.id=idc_user.user_id";
$c->condition = "idc_user.idc_id=$idc_id";

//运行后
object(CDbCriteria)#98 (12) { ["select"]=> string(1) "*" ["distinct"]=> bool(false) ["condition"]=> string(17) "idc_user.idc_id=6" ["params"]=> array(0) { } ["limit"]=> int(-1) ["offset"]=> int(-1) ["order"]=> string(0) "" ["group"]=> string(0) "" ["join"]=> string(38) "JOIN idc_user on t.id=idc_user.user_id" ["having"]=> string(0) "" ["with"]=> NULL ["alias"]=> NULL }

//User::model()->with('Idcs')->findAll($c)

//在ActiveRecord中，增加条件限制
$this->getDbCriteria()->mergeWith(array(
    'condition'=>"idc_id IN ($ids)",
));

 findByPk()method

Suppose your model name is “CompanyUnit”. Now you want to select data from there using PrimaryKey(PK). Then you can use “findByPk()” method in yiiframe. It is very easy and simple to use.
Example:
<?php
$comUnit = CompanyUnit::model()->findByPk(2);
echo $comUnit->name;
?>

DB select

Select data from  table with condition, it is very easy :
$command = Yii::app()->db->createCommand();
$chkSaleOrderProduct = $command->select(‘column_name’)->from(table_name‘)->where(“column_name=value”)->queryAll();
After running this code you can get result in
echo $chkSaleOrderProduct[0][column_name];
I think this code helps you.

I think it is very useful for new user in Yii Framework.
$command = Yii::app()->db->createCommand();
$command->insert(‘table_name’, array(‘coloumn_name’=>‘value’))