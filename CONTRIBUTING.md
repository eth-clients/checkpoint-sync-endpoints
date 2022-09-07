# Contributing

If you'd like to add your endpoint to the list please submit a PR. Please only list endpoints that are publicly available with relatively high uptime.

The structure of this project separates endpoints into their respective network YAML files located in [`endpoints/`](./endpoints/).

## Endpoint YAML schema

Each endpoint list item follows this schema;
```yaml
endpoint:
  # endpoint of the checkpoint sync
  endpoint: str()
  # list display name for this endpoint
  name: str()
  # if this endpoint provides entire finalized states
  state: bool()
  # if this endpoint provides an easy way for verifying the state downloaded from a different state provider
  verification: bool()
  # list of contacts
  contacts: list(include('contact'), min=0, max=5, required=False)
  # list of notes
  notes: list(include('contact'), min=0, max=5, required=False)

contact:
  # display or full name of contact
  name: str()
  # URL link to the contact page. eg. twitter/github link
  link: str(required=False)

note:
  # note description
  name: str()
  # URL link to related note. eg. twitter/github link
  link: str(required=False)
```

## Examples

Some common examples formatted in YAML

### Basic

Adding a mainnet endpoint involes appending endpoint data to [`endpoints/mainnet.yaml`](./endpoints/mainnet.yaml);
```yaml
- endpoint: https://checkpoint-sync.example.com
  name: example.com
  state: true
  verification: true
```

### Contacts

```yaml
- endpoint: https://checkpoint-sync.example.com
  name: example.com
  state: true
  verification: true
  contacts:
    - name: "@github"
      link: https://twitter.com/github
    # mailto link
    - name: "John Smith"
      link: "mailto:john.smith@example.com"
    # no link
    - name: "Jane Doe"
```

### Notes

```yaml
- endpoint: https://checkpoint-sync.example.com
  name: example.com
  state: true
  verification: true
  notes:
    - name: "Status page"
      link: https://checkpoint-sync-status.example.com
    # no link
    - name: "Some important note"
```

### Verification only endpoint

```yaml
- endpoint: https://checkpoint-sync.example.com
  name: example.com
  state: false
  verification: true
```

## Adding a new network

New networks can be added by simply creating a new file in `endpoints/{network}.yaml` and adding at least one endpoint.

## Lint locally

Requirements;
- Python 3.6+
- [Yamale](https://github.com/23andMe/Yamale)

```bash
# make sure yamale is installed
pip install yamale

# yamale lint
yamale -s schema.yaml endpoints
```
