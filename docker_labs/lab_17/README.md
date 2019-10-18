## Lab 17
To demonstrate `LABEL` instruction.

* We can add labels to our image to help organize images by project, record licensing information, to aid in automation, or for other reasons.
* For each label, add a line beginning with LABEL and with one or more key-value pairs.
* `LABEL` helps to add custom data into docker images.
* An image can have more than one label.
* We can specify multiple labels on a single line.
* Labels included in base or parent images (images in the FROM line) are inherited by our image.
* If a label already exists but with a different value, the most-recently-applied value overrides any previously-set value.
* To view an image’s labels, use the docker inspect command.
```
"Labels": {
                "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
            },
```
Above are labels from nginx:alpine image.

## Syntax
`LABEL <key>=<value> <key>=<value> <key>=<value> ...`

## Examples
```
LABEL "com.example.vendor"="ACME Incorporated"
LABEL com.example.label-with-value="foo"
LABEL version="1.0"
LABEL description="This text illustrates \
that label-values can span multiple lines."
```

Multiple labels using single `LABEL` instruction can be specified in following 2 ways,

`LABEL multilabel1="Label 1" multilabel2="Label 2" multilabel3="Label 3"`

```
LABEL \
    multilabel1="label 1" \
    multilabel2="label 2" \
    multilabel3="label 3"
```

## Commands
```
docker build -t inderpal2406/alpine-label:v0.0.1 .
docker inspect inderpal2406/alpine-label:v0.0.1 | less
```
