# ngOfflineModel - Your module for Offline operations with AngularJS

[![Build Status](https://travis-ci.org/willmendesneto/ngOfflineModel.png?branch=master)](https://travis-ci.org/willmendesneto/ngOfflineModel)
=================

## Installation

1 - Via bower

```bash
$ bower install ng-offline-model
```

2 - Clone this repository and access the generated folder

```bash
$ git clone git://github.com/willmendesneto/ngOfflineModel.git [project-name]
$ cd [project-name]
```
Once you have ngOfflineModel in your project, just include 'keepr.ngOfflineModel' as a dependency in your Angular application and you’re good to go. It's works!

```javascript
    angular.module('myModule', ['keepr.ngOfflineModel'])
```

3 - Methods:

- primaryKey: Primary Key that will be used for ngOfflineModel. This value will be unique;
- fields: Fields for mapp in ngOfflineModel. Only these chosen fields will be stored for the service;
- key: Key used for store locally (localStorage and sessionStorage are stored key value based);
- secret: Secret key for store;

4 - Methods:

- init: service contructor;
- createValueObject: Create the ValueObject of item for add/edit/list, based in `fields` attribute;
- setStorageType: set/update storageType (localStorage/sessionStorage);
- setKey: Set the storageType key for store in browser, based in key => value;
- getKey: Return the key used in this moment for ngOfflineModel instance;
- setListItems: Add default/first list items for store in storageType selected;
- getListItems: Return list items stored locally in browser;
- setFields: Set fields that ngOfflineModel will be map for store;
- countTotalItems: Return the count of totalItems, based in Primary Key;
- create: Create new item in list items stored locally;
- update: Update item stored locally in list items;
- delete: Remove item stored locally;
- clearAll: Clear all items stored locally, based in storageType;

5 - Example:

```javascript
var contactMock = [
  {_id: 1, name: 'Allan Benjamin', address: 'St. Claire Avenue, Nº 101', phone: '557188339933'},
  {_id: 2, name: 'Georgia Smith', address: 'St. Claire Avenue, Nº 102', phone: '557188339933'},
  {_id: 3, name: 'Gregory Levinsky', address: 'St. Claire Avenue, Nº 103', phone: '557188339933'},
  {_id: 4, name: 'Jackeline Macfly', address: 'St. Claire Avenue, Nº 104', phone: '557188339933'},
  {_id: 5, name: 'Joseph Climber', address: 'St. Claire Avenue, Nº 105', phone: '557188339933'},
  {_id: 6, name: 'Joshua Jackson', address: 'St. Claire Avenue, Nº 106', phone: '557188339933'}
];

var params = {
  key: 'contactMock', // localStorage/sessionStorage key
  primaryKey: '_id', // primary field. This field will be increased automatically
  fields: ['_id', 'name', 'address', 'phone'] // Fields mapped for store
};

var ContactModel = ngOfflineModel.setStorageType('localStorage')
                                  .init(contactMock, params);

ContactModel.getListItems(); // return contactMock value;
ContactModel.getKey(); // return 'contactMock';
ContactModel.countTotalItems(contactMock); // === contactMock.length;


// Create an item
var contact = {
  name: 'This is a test',
  address: 'Adress test',
  phone: '557188998877'
};
ContactModel.create(contact);

// Update the item
contact = {
  phone: '559554138698',
  _id: 7 // This field is verified based in `primaryKey` attribute value
};
ContactModel.update(contact);

// Removing the item
ContactModel.delete(7);

// Removing all items of storage
ContactModel.clearAll();
```

## Author

**Wilson Mendes (willmendesneto)**
+ <https://plus.google.com/+WilsonMendes>
+ <https://twitter.com/willmendesneto>
+ <http://github.com/willmendesneto>


New features comming soon.
