
What, if any, changes do we make to `coordinateTransformation`s inside NGFF multiscales.datasets.
Here are the three options, as I see them.

Unless there is broad consensus otherwise, we'll go with the "permissive" option.

## permissive 

Summary: `coordinateTransformation`s in a `dataset` have an `input` field, it is ignored, but SHOUD equal the `path` value.

* Pros
    * Little extra work 
    * "innocent mistakes" are still valid
* Cons
    * May contain extraneous / misleading information

### Example

NGFF multiscales dataset:

Valid, recommended example:
```
{
    "path" : "0",
    "coordinateTransformation" : {
        "type" : "scale",
        "scale": [2, 3],
        "input": "0",
        "output": "org.alleninstitute.CCFv1"
    }
}
```

Valid, not recommended example:
```
{
    "path" : "0",
    "coordinateTransformation" : {
        "type" : "scale",
        "scale": [2, 3],
        "input": "the cow says moo",
        "output": "org.alleninstitute.CCFv1"
    }
}
```

## restrictive

Summary: `coordinateTransformation`s in a `dataset` have an `input` field, it MUST equal the `path` value.

* Pros
    * Zero extra work 
    * super explicit
* Cons
    * Information is duplicated.
    * "innocent mistakes" have invalid results

### Example

NGFF multiscales dataset:

Valid example:
```
{
    "path" : "0",
    "coordinateTransformation" : {
        "type" : "scale",
        "scale": [2, 3],
        "input": "0",
        "output": "org.alleninstitute.CCFv1"
    }
}
```

Invalid example:
```
{
    "path" : "0",
    "coordinateTransformation" : {
        "type" : "scale",
        "scale": [2, 3],
        "input": "the cow says moo",
        "output": "org.alleninstitute.CCFv1"
    }
}
```


## structural

Summary: `coordinateTransformation`s in a `dataset` MUST not have an `input` field,
it is implicitly understood to equal the `path` value.

* Pros
    * No duplication or extraneous information
* Cons
    * Two different transformation schema (one for in a `dataset`, another elsewhere)
    * Most extra work 
    * "innocent mistakes" (including `input`) are invalid

### Example

NGFF multiscales dataset:

Valid example:
```
{
    "path" : "0",
    "coordinateTransformation" : {
        "type" : "scale",
        "scale": [2, 3],
        "output": "org.alleninstitute.CCFv1"
    }
}
```
Invalid example:
```
{
    "path" : "0",
    "coordinateTransformation" : {
        "type" : "scale",
        "scale": [2, 3],
        "input": "0",
        "output": "org.alleninstitute.CCFv1"
    }
}
```

Invalid example:
```
{
    "path" : "0",
    "coordinateTransformation" : {
        "type" : "scale",
        "scale": [2, 3],
        "input": "the cow says moo",
        "output": "org.alleninstitute.CCFv1"
    }
}
```

