---
title: "Microflow"
parent: "Microflows"
space: "Reference Guide 5"
---


<div class="alert alert-warning">{% markdown %}

This document describes the properties of a microflow. If you want to see what microflows are for and what kind of elements they contain, you can check the [Microflows](Microflows) overview documentation.

{% endmarkdown %}</div>

## Common Properties

### Name

The internal name of the microflow.

### Folder

The folder in which the microflow is located in the project.

## Concurrent Execution Properties

### Disallow

With this property you can specify whether it is allowed for the microflow to be executed more than once concurrently. This applies to all users at the same time.

<table><thead><tr><th class="confluenceTh">Option</th><th class="confluenceTh">Description</th></tr></thead><tbody><tr><td class="confluenceTd">False</td><td class="confluenceTd">It is possible to execute the microflow more than once concurrently.</td></tr><tr><td class="confluenceTd">True</td><td class="confluenceTd">It is not possible to execute the microflow more than once concurrently; the user receives a message or another microflow is executed instead.</td></tr></tbody></table>

Disallowing concurrent execution of a microflow is useful if a microflow would interfere with another running instance. For example, if it accesses a global resource.

### Error message

Error message defines the message the user gets when concurrent execution is not allowed and the user tries to start the microflow while it is already being executed.

### Error Microflow

Error microflow defines which microflow is executed when concurrent execution is not allowed and the user tries to start the microflow while it is already being executed. When set, there will be no further message shown to the user.

## Output Properties

### Return type

The return type defines what information the microflow returns. The caller of the microflow will get a result of this type.

<div class="alert alert-info">{% markdown %}

A microflow could return whether or not the committing of an object should continue. In this case, a boolean would be the return type of the microflow.

{% endmarkdown %}</div>

## Security Properties

### Allowed roles

Allowed roles defines to which [module role](Module+Role) the user must have to be able to execute the microflow.

<div class="alert alert-warning">{% markdown %}

Note that these roles are only checked when the microflow is executed from the client. A microflow is always allowed to call another microflow and these roles are not checked then.

{% endmarkdown %}</div>

See also [Module Security](Module+Security).

### Apply entity access

This property indicates whether entity access based on the current user is applied when performing operations on objects. Applying entity access limits the objects that are retrieved by the [retrieve action](Retrieve) to only those that the current user is allowed to see. Similarly, to reading and writing attributes and associations the entity access of the current user is applied. If entity access is not applied on the other hand, all operations are allowed and all objects are retrieved.

<div class="alert alert-warning">{% markdown %}

Microflows that apply entity access have a yellow background; microflows that do not have a white background.

{% endmarkdown %}</div><table><thead><tr><th class="confluenceTh">Option</th><th class="confluenceTh">Description</th></tr></thead><tbody><tr><td class="confluenceTd">Yes</td><td class="confluenceTd">Entity access is applied to retrieving and manipulating objects. The rights of current user are taken into account.</td></tr><tr><td class="confluenceTd">No</td><td class="confluenceTd">Entity access is not applied.</td></tr></tbody></table><div class="alert alert-success">{% markdown %}

By default entity access is not applied. Set 'apply entity access' to true if you want to perform some actions that respect the rights of the current user.

{% endmarkdown %}</div>

_Default value:_ No

## Usage Properties

### Mark as used

You can search for unused items (Ctrl+Shift+F, Search for = Unused items) in the Modeler. Microflows that are only called from Java code will be listed as unused because the Modeler cannot look inside Java source code.

By setting the propery 'Mark as used' to 'Yes' you specify that the document is used implicitly and the Modeler will no longer list it when searching for unused items.

_Default value:_ No
