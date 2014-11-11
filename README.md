angular-resource.ms
============================

An AngularJS module that provides a resource-generation service similar to ngResource, but optimized for the
Django REST Framework. Based on ngResource 1.3.x and [djResource](https://github.com/blacklocus/angular-django-rest-resource). The biggest features:

* The `isArray` methods like `query` allow for paginated responses. The pages will be streamed into the promise object.

Installation
------------
Download angular-resource.ms.js and put it in your project. 

Usage
-----
Do this somewhere in your application HTML:

    <script src="angular-resource.ms.js"></script>

Add this AngularJS module as a dependency to your AngularJS application:

    angular.module('app', [..., 'ngResource']);

(where 'app' is whatever you've named your AngularJS application).


In your controllers and anything that needs to interact with the Django REST Framework services, inject the `$resource`
service. Then you can create class-like objects that represent (and interact with) your Django REST Framework resources:

    var Poll = $resource('/polls/:pollId/', {pollId:'@id'});

    var myPoll = Poll.get({pollId:86}, function() {
        myPoll.readByUser = true;
        myPoll.$save();
    });

For complete API, consider the documentation for [$resource](http://docs.angularjs.org/api/ngResource.$resource), as
this module follows the API quite closely.
