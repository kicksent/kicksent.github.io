---
layout: projects
author_profile: true
categories: projects
---

# Shakespeare Sonnet and Writer API Documentation (You found the "...")

(This project is not yet live online) 
**Basic Functionality:**  
This API will offer all 154 Shakespeare Sonnets   
**Later on:**  
Eventually it will also generate Sheakespearean Sonnets using a program I wrote in college for English. 

## Usage

All responses will have the form 

```json
{
    "data": "Mixed type holding the content of the response"
    "message": "Description of what happened"
}
```


Subsequent definitions will only detail the expected value of the 'data field'

### List all available Sonnets
**Definition**
`GET /sonnets`
**Response**
-`200 OK` on success

```json
[
    {
        "identifier": "1",
        "name": "Sonnet I",
        "sonnet-type": "Shakespeare",
        "first_four_words": "From fairest creatures we",
        "full-text": "Sonnet Text"
    }
    {
        "identifier": "2",
        "name": "Sonnet II",
        "sonnet-type": "Shakespeare",
        "first_four_words": "When forty winters shall",
        
    }

]
 ```

### Create a new sonnet

**Definition**

`POST /Sonnets`

**Arguments**

- `-"identifier":string` a globally unique identifier for the sonnet
- `"name": string` the name of the sonnet
- `"sonnet_type": string` type of sonnet or tag of sonnet
- `"first_four_words": string` the first four words of the sonnet
- `"full_text": "Sonnet Text"` full text

If a sonnet with the given identifier already exists, the existing sonnet will be overwritten.

**Response** 

-`201 Created` on success

```json
[
    {
        "identifier": "1",
        "name": "Sonnet I",
        "sonnet_type": "Shakespeare",
        "first_four_words": "From fairest creatures we",
        "full_text": "Sonnet Text"
    }
]
 ```

 ##Lookup sonnet details

 `GET /sonnet/<identifier>`

 **Response**

- `404 Not Found` if the sonnet does not exist
- `200 OK` on success

```json
[
    {
        "identifier": "1",
        "name": "Sonnet I",
        "sonnet_type": "Shakespeare",
        "first_four_words": "From fairest creatures we",
        "full_text": "Sonnet Text"
    }
]
```

## Delete a sonnet

**Definition

`DELETE /sonnet/<identifier>`

**Response**

- `404 Not Found` if the sonnet does not exist
- `204 OK` success no content
