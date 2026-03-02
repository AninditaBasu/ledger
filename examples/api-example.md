---
layout: api
title: Static API page
description: This API returns the word definitions of nouns in vedic literature.
---

{% for ep in site.data.api.endpoints %}
## <span class="method">{{ ep.method }}</span> {{ ep.path }}

{{ ep.description }}

{% endfor %}