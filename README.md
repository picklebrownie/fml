# FML
Form Management for Life. 

## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Schema](#schema)
* [Setup](#setup)
* [Developer Notes](#developer-notes)
* [Resources](#resources)

## General info
Goal is to manage forms on a large scale. 
With this application, in-house users will first define and group form fields into containers. Each form field has an optional `condition` parameter, an array of strings to use in mapping the form formfields to customer users based on the conditional user settings. 
	
## Technologies
Project is anticipated to be created with:
* Gatsby
* GraphQL
* MongoDB
	
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

## Resources

* "Nesting GraphQL With MongoDB" by [Jenny Yang](https://medium.com/swlh/nesting-graphql-with-mongodb-1013361176c1)
* "How to write a good README for your GitHub project?" by [Rita Łyczywek](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)
* [MongoDB Dataypes](https://www.tutorialspoint.com/mongodb/mongodb_datatype.htm)
* W3Schools [form tag](https://www.w3schools.com/tags/tag_form.asp) and [input tag](https://www.w3schools.com/tags/tag_input.asp)
* [MongoDB Data Modeling Introduction](https://docs.mongodb.com/manual/core/data-modeling-introduction/)