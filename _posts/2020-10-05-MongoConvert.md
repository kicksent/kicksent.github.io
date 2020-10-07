---
layout: posts
title: Mongo convert schema to nested
---
# The problem: 

Due to how I currently have the DB configured, dependent children must be updated when the parent is updated. 
Restaurant field must be updated in other objects if the name is updated in restaurants model. 
Menu field must be updated in other objects if the name is updated in menu model. 
MenuSection field must be updated in other objects if the name is updated in menuSection model. 
etc...

There's also the problem that if the children are updated then I can't change what they are pointing to unless I update both the theoretical child and parent. (Theoretical since they realy don't have any association in the database anyway.)


### menu-model.js
```
const Menu = new Schema(
    {
        menuSections: {[MenuSection]}
        name: { type: String, required: true },
        type: { type: String, required: false },
        restaurant: { type: String, required: true },
    },
    { timestamps: true },
)
```
### menuItem-model.js
```
const MenuItem = new Schema(
    {
        name: { type: String, required: true },
        description: { type: String, required: false },
        price: { type: Number, required: true},
        photoUrl: { type: String, required: false},
        rating: { type: Number, required: false},
        restaurant: { type: String, required: true},
        menuSection: { type: String, required: true},
        menu: { type: String, required: true },
        enabled: { type: Boolean, required: true, default: true},
        ownerDisabled: { type: Boolean, required: true, default: false},
        hearts: { type: Number, required: false },
        bookmarks: { type: Number, required: false },
    },
    { timestamps: true },
)

```
### menuSection-model.js
```
const MenuSection = new Schema(
    {
        name: { type: String, required: true },
        note: { type: String, required: false },
        restaurant: { type: String, required: true },
        menu: { type: String, required: true },
    },
    { timestamps: true },
)
```

## New Restaurant model in one file with nesting

This is what I want. The nesting allows me to update the restaurant name and it will update everywhere in my application like it should. I should have done this from the start but I wanted to keep it simple for the MVP to keep myself from focusing too hard on database design. My goal for this project is to get better at React. 

### restaurant-model.js
```
const mongoose = require('mongoose')
const Schema = mongoose.Schema

const Restaurant = new Schema(
    {
        // Don't trust index, enforce this in the controller too
        name: { type: String, unique: true },
        address1: { type: String, required: true },
        address2: { type: String, required: false },
        rating: { type: Number, required: false },
        menus: [Menu],
    },
    { timestamps: true },
)

const Menu = new Schema(
    {
        menuSections: [MenuSection],
        name: { type: String, required: true },
        type: { type: String, required: false },
    },
    { timestamps: true },
)

const MenuSection = new Schema(
    {
        menuItems: [MenuItem],
        name: { type: String, required: true },
        note: { type: String, required: false },
    },
    { timestamps: true },
)

const MenuItem = new Schema(
    {
        name: { type: String, required: true },
        description: { type: String, required: false },
        price: { type: Number, required: true},
        photoUrl: { type: String, required: false},
        rating: { type: Number, required: false},
        enabled: { type: Boolean, required: true, default: true},
        ownerDisabled: { type: Boolean, required: true, default: false},
        hearts: { type: Number, required: false },
        bookmarks: { type: Number, required: false },
    },
    { timestamps: true },
)
```

## Exporting from mongo, and converting using python
Export the models to json format using mongo, import them as a module, and then iterate the objects and generate a new json object which we can insert into our new restaurant model. 

```
import json
from menu_items import *
from menu_sections import *
db_dict = {}
for item in menu_items:
    db_dict[item["restaurant"]] = {}

for item in menu_items:
    if("menus" not in db_dict[item["restaurant"]]):
        db_dict[item["restaurant"]]["menus"] = {}
    db_dict[item["restaurant"]]["menus"][item["menu"]] = {}

for item in menu_items:
    if("menuSections" not in db_dict[item["restaurant"]]["menus"][item["menu"]]):
        db_dict[item["restaurant"]]["menus"][item["menu"]]["menuSections"]= {}
    db_dict[item["restaurant"]]["menus"][item["menu"]]["menuSections"][item["menuSection"]] = {}

for item in menu_items:
    if("menuItems" not in db_dict[item["restaurant"]]["menus"][item["menu"]]["menuSections"][item["menuSection"]]):
        db_dict[item["restaurant"]]["menus"][item["menu"]]["menuSections"][item["menuSection"]]["menuItems"] = {}    
    db_dict[item["restaurant"]]["menus"][item["menu"]]["menuSections"][item["menuSection"]]["menuItems"][item["name"]] = {
        "name": item["name"], "description": item["description"], "price": item["price"]
    }

for item in menu_sections:
    db_dict[item["restaurant"]]["menus"][item["menu"]]["menuSections"][item["name"]]["note"] = item["note"]
    break

#There's only two restaurants in my collection, so I just hard coded these to move them but this could also have been done for these cases too...

db_dict["Morning Glory Cafe"]["address1"] = "111 Baseline Road"
db_dict["Test Cafe"]["address1"] = "111 Test Road"

json_formatted_str = json.dumps(db_dict, indent=2)

print(json_formatted_str)
```
### db_convert.py


