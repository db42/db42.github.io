---
layout: post
title: Facebook Messenger chat bot - 403 forbidden error
---

Here's the JSON response for an error when Send API request fails. This happens when the user has deleted the conversation thread with your chatbot.


```
Failed calling Send API 403 Forbidden { message: '(#200) This person isn\'t receiving messages from you right now.',
  type: 'OAuthException',
  code: 200,
  error_subcode: 1545041,
  fbtrace_id: 'G3wkMuClPvR' }
Successfully sent message with id xxx to recipient yyy
```

Reference: [Messenger platform error docs](https://developers.facebook.com/docs/messenger-platform/send-api-reference#errors)
