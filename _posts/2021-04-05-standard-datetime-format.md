---
layout: post
title:  Standard DateTime Format
date:   2021-04-05 11:00:30 +0100
categories: api-standards events
status: accepted
---

This decision cover the string format for `date-time` objects when used in events or API request/responses

### Context

Within JSON API's date and date time objects are strings - so it's important to define a transfer format so API consumers know how to easily parse and process dates emitted

### Decision

The standard format is based on ISO8601 and uses UTC time.

{% highlight javascript %}
yyyy-MM-ddTHH:mm:ss.fffZ

// example

const event = new Date('05 October 2011 14:48 UTC');
console.log(event.toISOString());
// expected output: 2011-10-05T14:48:00.000Z
{% endhighlight %}

### Consequences

This format recorsd time down to the millisecond which may be too precise for some circumstances, in this case it's acceptable to round up to the nearest second by settngs the milsecond time to 000.

User must use UTC time and not GMT times as local time can vary across system boundaries and so standaidising to UTC avoids amiguity about the time of an event. 