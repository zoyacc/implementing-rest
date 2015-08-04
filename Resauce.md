# "Resauce Framework" #
Resauce is a small extension to Zend Framework. It gives you a lightweight framework for building RESTful HTTP interfaces with PHP.

## Introduction ##

The main idea is to treat each controller as a Resource; i.e. a controller is responsible for **one resource**. This is distinct from other solutions (such as the REST components included in ZF itself) where a controller is responsible for both collection and item resources.

Example Routes:

'/blog' >> BlogController

'/blog/:post' >> BlogPostController

'/blog/:post/comments' >> BlogPostCommentsController

A route in a Resauce application simply maps a URI pattern to a Resauce controller - no controller action should ever be specified in a route. Instead - controller actions are 'routed' according to the HTTP method of a given request.

i.e.

  * GET >> getAction()
  * PUT >> putAction()
  * POST >> postAction()
  * DELETE >> deleteAction()
  * HEAD >> headAction()
  * OPTIONS >> optionsAction()

If a request is routed to a resauce controller which does not have an action implemented for the given HTTP method, then the Resauce will automatically respond with a 405 Method Not Allowed response code.

## So what? ##

The Resauce approach provides much more flexibility over how resources can be exposed than other alternatives - you have complete control of URI patterns and each resource's HTTP methods.

REST is **not** collection/item CRUD; frameworks/components which don't recognize this are introducing needless restriction - the only 'benefit' of which is that your collection and item resources can be handled in one controller and with one route.

## Example Usage ##

Configure routing for your interface by creating an _initRoutes function in your Resauce Bootstrap._

application/Bootstrap.php:
```
<?php
class Bootstrap extends Resauce_Application_Bootstrap
{
	public function _initRoutes() {
		$this->addResauceRoutes(array(
			'blog' => 'blog',
			'blog/:post' => 'blog-post',
			'blog/:post/comments' => 'blog-post-comments'
		));
	}
}
```

Then create the controllers in the controller directory, with Actions for HTTP methods you want the URI to support:

e.g. application/controllers/BlogController.php
```
<?php
class BlogController extends Resauce_Controller_Resource
{
	// Action for handling GET requests i.e. GET /blog
	public function getAction() {
		// fetch list of posts, add them to view, render the view
	}
	// Action for handling POST requests i.e. POST /blog
	public function postAction() {
		// create new post
	}
}
```

For the routes in the example Boostrap above - you will also need to create the other controllers:

BlogPostController.php
BlogPostCommentsController.php