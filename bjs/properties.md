# Properties

## Introducing

It is possible to save data in bot. Data can be numeric, text, datetime and etc.

For example:

* Bot can have DailyBonus saved in bot prop (it is global for all bot)
* User can have Balance saved in user prop (it is personall)

{% hint style="info" %}
Properties can be belong for user or for bot.
{% endhint %}

## Types

Properties can be:

* integer, e.g.: `150`
* float, e.g.: `5.5`&#x20;
* boolean: `true, false`
* string, e.g.: `"Hello world"`
* text, e.g.: `"it is very big text ..... 1000 symbols here or more"`
* json, e.g.: `{ any: "data", here: "can", be: {used: true}, with: ["array", "too"] }`
* datetime, e.g: `new Date()`



## Set property

```javascript
// set global prop
Bot.setProp({ name: 'myProp', value: 15 });
 
// set JSON prop for user
User.setProp({
 name: 'BIO',
 value: { email: "test@example.com", age: 10 }
});
```

{% hint style="success" %}
* so for global prop use `Bot.xxx` method
* for user's prop use `User.xxx` method
{% endhint %}

{% hint style="info" %}
You can use short naming also: `Bot.setProp`, `User.setProp`
{% endhint %}

also you can use old style:

```javascript
 // set global prop
Bot.setProperty("myProp", 15, "float");
```

### Set prop for other user by id

```javascript
 // set global prop
Bot.setProp({
  name: 'otherUserProp',
  value: "test Prop",
  // you can pass other user.id for saving user prop for other user
  user_id: other_user.id
});
```

### Set prop for other user by telegramid

```javascript
 // set global prop
Bot.setProp({
  name: 'otherUserProp',
  value: "test Prop",
  // you can pass other user.id for saving user prop for other user
  user_telegramid: other_user.telegramid
});
```

{% hint style="success" %}
You can set (or read) property via bot\_id and read (or set) it via telegramid. It doesn't matter and it will be the same value.
{% endhint %}

### You can save prop in the List

Please read this [article](lists/)



## Get property

```javascript
// get global prop
var myProp = Bot.getProp('myProp');
Bot.sendMessage("prop: " + myProp);
 
// get prop for user
var bio = User.getProp('BIO');
Bot.sendMessage("Hello, " + bio);
```

or get prop with default value:

```javascript
// prop by default will be 15
var myProp = Bot.getProp('myProp', 15);
```

{% hint style="info" %}
You can use short naming also: `Bot.getProp`, `User.getProp`
{% endhint %}

### Getting other user's prop:

{% hint style="info" %}
Your bot must have this user
{% endhint %}

```javascript
// get prop for other user
var bio = Bot.getProp({
  name: 'BIO',
  // you can pass other user.id for getting other user prop
  user_id: other_user_id
  // or by telegramid:
  // user_telegramid: other_user_telegramid
});
```

{% hint style="success" %}
You can set (or read) property via bot\_id and read (or set) it via telegramid. It doesn't matter and it will be the same value.
{% endhint %}

###

### Getting other bot prop for current user:

{% hint style="info" %}
Your account must have this bot
{% endhint %}

```javascript
// get other bot prop for cur user
var bio = Bot.getProp({
  name: 'BIO',
  bot_id: other_bot_id  // available via bot.id
  // if needed:
  // user_id: userID // for user's prop
  // user_telegramid: tgID // for user by telegramid
});
```



### Getting other bot prop for other user:

{% hint style="info" %}
Your account must have this bot with this user
{% endhint %}

```javascript
// get other bot prop for cur user
var bio = Bot.getProp({
  name: 'BIO',
  bot_id: other_bot_id  // available via bot.id
  // you can pass other user.id for getting other user prop
  user_id: other_user_id
});
```



## Delete property

```javascript
// prop "myProp" will be removed
Bot.deleteProp("myProp");
```

Then `null` passing to prop's value is delete property also:

```javascript
// prop "myProp" with null value will be removed
Bot.setProp("myProp", null, "float");
```



