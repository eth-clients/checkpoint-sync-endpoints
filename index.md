---
layout: default
---

This page contains a community maintained list of Ethereum Beacon Chain checkpoint sync endpoints.

> ⚠️ This list should not be treated as a single source of truth for these endpoints, or the data they provide. It is a community maintained list, and as such, it is possible that some of the endpoints listed here are not up to date, or are not providing the data they claim to be providing.

Endpoints can provide 2 main functions:
- `state` providers - those who provide entire finalized states
- `verification` providers - those who provide an **easy** way for verifying the state downloaded from a `state` provider.

If you'd like to add your endpoint to the list please read the [documentation]({{ site.github.repository_url }}/blob/main/CONTRIBUTING.md).

## Endpoints
Note: pick a random `state` provider, and verify your sync against multiple random `verification` providers for the same network.

Networks:
{% for network in site.data.endpoints %}
  - [{{network[0] | capitalize}}](#{{network[0]}})
{% endfor %}

{% for network in site.data.endpoints %}
{% assign endpoints = network[1] | sample:99999 %}
### {{network[0] | capitalize}}

| Name      | State | Verification |                  Endpoint                   |            Contact details             | Notes |
|:----------|:------|:-------------|:--------------------------------------------|:---------------------------------------|:------|{% for endpoint in endpoints %}
| {{endpoint.name}} | {% if endpoint.state %}✅{% else %}❌{% endif %} | {% if endpoint.verification %}✅{% else %}❌{% endif %} | [{{endpoint.endpoint}}]({{endpoint.endpoint}}) | {% if endpoint.contacts %}{% for contact in endpoint.contacts %}{% if contact.link %}[{{contact.name}}]({{contact.link}}){% else %}{{contact.name}}{% endif %} {% endfor %}{% endif %} | {% if endpoint.notes %}{% for note in endpoint.notes %}{% if note.link %}[{{note.name}}]({{note.link}}){% else %}{{note.name}} {% endif %}{% endfor %}{% endif %} |{% endfor %}

{% endfor %}
