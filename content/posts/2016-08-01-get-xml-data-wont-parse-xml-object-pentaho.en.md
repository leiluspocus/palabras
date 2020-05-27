---
title: Get XML Data won't parse XML object Pentaho
date: "2016-08-01T17:20:40+00:00"
template: post
draft: false
slug: /en/get-xml-data-wont-parse-xml-object-pentaho/
category: ETL
tags:
  - etl
  - pentaho
---

I had an issue with Pentaho today. It wasn&rsquo;t able to simply parse this XML that I was fetching from Amazon Marketplace Webservice.

Here&rsquo;s the data I got :

```
<SubmitFeedResponse xmlns="http://mws.amazonaws.com/doc/2009-01-01/">
<SubmitFeedResult>
<FeedSubmissionInfo>
<FeedSubmissionId>MY_FEED_ID</FeedSubmissionId>
<FeedType>_POST_INVENTORY_AVAILABILITY_DATA_</FeedType>
<SubmittedDate>2016-08-01T19:28:30+00:00</SubmittedDate>
<FeedProcessingStatus>_SUBMITTED_</FeedProcessingStatus>
</FeedSubmissionInfo>
</SubmitFeedResult>
<ResponseMetadata>
<RequestId>MY_REQUEST_ID</RequestId>
</ResponseMetadata>
</SubmitFeedResponse>
```

The step « Get XML Data » couldn&rsquo;t parse it because of the xmlns attribute tag. So I had to add a step « Replace in string » that would delete this attribute.
