# FML
Form Management for Life. 

## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Schema](#schema)
* [Setup](#setup)
* [Developer Notes](#developer-notes)
* [References](#references)

## General info
Goal is to manage forms on a large scale. 
With this application, in-house users will first define and group form fields into containers. Each form field has an optional `condition` parameter, an array of strings to use in mapping the form formfields to customer users based on the conditional user settings. 
	
## Technologies
Project is anticipated to be created with:
* Gatsby
* GraphQL
	
## Schema

```
Form {
    name
    action
    method
    target
    containers : [ Container ]
}

Container {
    name
    title
    description
    groups : [ Group ]
}

Group {
    name
    header
    description
    tooltip
    fields : [ Field ]
}

Field {
    inputType
    category
    name
    placeholder
    tooltip
    confirm
    values : [
        {
            value
            label
            tooltip
            checked
            disabled
        }
    ]
    max
    maxlength
    pattern
    readonly
    required
    autocomplete
    condition: [ condition.ObjectId ]
}

Condition {
    name: { type: String },
    value: { type: String },
    forms: [ Form.ObjectId ]
}
```

## Setup
Nothing, yet. Stay tuned, Folks.

## Developer Notes

* If inputType is text| number | hidden | date then values is an array of ONE value and checked must be false
* Consider storing the settings in the front end so the user doesn't have to use data to get thier form fields every time.
* create middleware to handle data validation. The middleware would also be responsible for setting the flags that let the frontend know that changes have been made to the user form field settings.
* confirm will let the front end know that we need to ask the user to input the data twice

## References

