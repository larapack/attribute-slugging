# attribute-slugging
Allows your Eloquent Model to automatically generate a unique slug for a attribute on save.

## Installing

Install using Composer `composer require larapack/attribute-slugging 1.*`.

## Usage

First add the trait `Slugable` to your Eloquent Model.
```
<?php

namespace App;

use Larapack/AttributeSlugging/Slugable;

class User
{
  use Slugable;
  
  /**
   * @var array List of attribute names which should be slugged
   */ 
  protected $slug = [
    'username_slug' => 'username', // set the attribute names you which to slug and from what attribute it should be generated from
  ];
  
  //...
}
```

Test:
```
// we make two user objects
$userA = new App\User;
$userB = new App\User;
// then we set both username's to "Mark"
$userA->username = "Mark";
$userB->username = "Mark";
// save both objects
$userA->save();
$userB->save();
// now the unique slugs have been set
echo $userA->username_slug; // outputs "mark"
echo $userB->username_slug; // outputs "mark-2"
```
