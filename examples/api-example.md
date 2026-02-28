---
layout: api
title: REST API
description: Simple JSON endpoints for Ledger
---

# {{ page.title }}

{{ page.description }}

{% for ep in site.data.api.endpoints %}
## <span class="method">{{ ep.method }}</span> {{ ep.path }}

{{ ep.description }}

{% endfor %}