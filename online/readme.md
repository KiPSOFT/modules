# Online counter

- this module counts online users (according the cookies)
- read statistics for the period (daily, monthly, yearly)
- easy use in views
- module stores data into the database directory as plain text
- module is resists at the restart app
- __IMPORTANT:__ this module do not work with the cluster

## Properties

### online.online

> Count of online users.

```js
var online = framework.module('online');
console.log(online.online);
```

```html
Online: <b>@{online}</b>
```

### online.today

> Today statistisc.

```js
var online = framework.module('online');
var today = online.today;

today.hits;       // page hits per day (impressions)
today.unique;     // unique users per day
today.count;      // users count per day
today.search;     // search traffic (according the referer header or utm_medium param) per day
today.social;     // social network traffic (according the referer header or utm_medium param) per day
today.direct;     // direct traffic per day
today.unknown;    // other traffic per day
today.mobile;     // mobile devices per day (unique)
today.desktop;    // desktops per day (unique)
```

### online.xhr

> Allow XHR requests. Default: __true__.

```js
var online = framework.module('online');

online.xhr = false;
```

## Methods

### online.daily(callback)

> Daily stats.

```js
var online = framework.module('online');

online.daily(function(stats) {
	
	// collection of stats
	console.log(stats);

});

```

### online.monthly(callback)

> Monthly stats.

```js
online.monthly(function(stats) {
	
	// object of stats
	// Object.keys(stats);
	console.log(stats);

});
```

### online.yearly(callback)

> Yearly stats.

```js
online.yearly(function(stats) {
	
	// object of stats
	// Object.keys(stats);
	console.log(stats);

});
```

## Delegates

### online.onValid(req);

```js
var online = framework.module('online');

// default settings
online.onValid = function(req) {
	return true;
};
```

## Events

### online.on('online')

> New online user.

```js
var online = framework.module('online');

online.on('online', function(req) {
	
});
```

### online.on('change')

> Online count is changed.

```js
online.on('change', function(count) {

});
```