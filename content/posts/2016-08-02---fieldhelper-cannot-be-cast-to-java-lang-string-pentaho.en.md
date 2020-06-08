---
title: Pentaho - FieldHelper cannot be cast to java.lang.String
date: "2016-09-01T13:11:20+00:00"
template: post
draft: false
slug: "/en/pentaho-field-helper-cannot-be-cast"
category: "ETL"
tags:
  - "java"
  - "pentaho"
---


> 👴 _Careful_ You're reading an old article ! Some links might be broken and content may be outdated

I had the following error in a « User Defined Java Class » step on Pentaho Data Integration.

```
FieldHelper cannot be cast to java.lang.String
```

Indeed, you have to use the getRow() method to convert the field you&rsquo;re getting into a String or any other variable type.

```java
public boolean processRow(StepMetaInterface smi, StepDataInterface sdi) throws KettleException, Exception
{
  Object[] r = getRow();
        if (r == null) { return false; }
        String myString = get(Fields.In, "FeedSubmissionId").getString(r);
}
```