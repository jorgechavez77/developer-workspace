---
layout: post
title:  "AWS Lambda Functions"
date:   2019-06-21 21:00:44 -0400
categories: AWS Lambda
---

### Here I will show how to create a AWS lambda from scratch.

1. __Create a Lambda Role__

First, Log on __AWS Console__. After you are logged in you will see on the top menu bar the top left the word __Services__, click on it and search for `IAM`.

On the left panel look for `Roles` click it then click `Create role`. You will have a big selection of services.
For now just select __Lambda__ then click `Next: Permissions`.

Type _lambda_ and look for `AWSLambdaBasicExecutionRole` click `Next: Tags` add any tag you would like.

Name the role __my-lambda-role__ or any name that make sense for you, write any description you'd like and click on `Create role`.

1. __Create a Lambda Function__

Go to `services` and search for `lambda`. Click on `create function`, select `Author from scratch`, name your function and select your programming language of preference, in my case I will select `NodeJS`.

```javascript
const fn = param => {
  if (param) return true
}
```
