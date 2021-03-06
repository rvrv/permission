Permission is [Express](http://expressjs.com/) & [Passport](http://passportjs.org/)-compatible authorization
middleware for [Node.js](http://nodejs.org/).

## Install

    $ npm install permission


## Usage

#### Fast start
It is as simple as `require('permission')`, because you do want to _require permission_, don't you? Don't mess your model nor view with control-specific logic. Pass middleware determing which roles user needs to have!

	router.get('/', require('permission')(['admin']), function(req, res) {
    	res.render('stats');
	})

Pass an array determining which roles one controller supports. 
Leave empty if you want to allow any role to be authorized, but still to be authenticated (signed in).
Pass an empty array to ensure nobody has access, even when authenticated. 

	router.get('/', require('permission')(), function(req, res) {
    	res.render('profile');
	})


Fill out array with more roles, if needed.

	router.get('/', require('permission')(['admin', 'user']), function(req, res) {
    	res.render('schools');
	})


#### Advantage start
There are 2 default values in _permission_ module:
- role property
- route for no permission

Default role property is searched in Express' user role property, `req.user.role`. 
If the user doesn't have permission, a 401 is returned. You can also setup a redirection.

To override these 2 values, do the following on your `app` configuration:

	app.set('permission', {role: 'myRole', noPermissionRedirect: '/myRedirectRoute'});


## Contribution
If you want to suggest something, make a pull request or contribute in any other form,
you're welcome to do so @ GitHub's [repository](https://github.com/ttenodi/permission).

*Please note:* This is young module and it will develop soon to satisfy more use cases.