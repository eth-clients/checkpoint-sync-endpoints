# Ethereum Beacon Chain checkpoint sync endpoints

This repository contains a community maintained list of Ethereum Beacon Chain checkpoint sync endpoints.

> :warning: This list should not be treated as a single source of truth for these endpoints, or the data they provide. It is a community maintained list, and as such, it is possible that some of the endpoints listed here are not up to date, or are not providing the data they claim to be providing.

Endpoints can provide 3 main functions:
- `state` providers - those who provide entire finalized states
- `verification` providers - those who provide an **easy** way for verifying the state downloaded from a `state` provider.
- `block` providers - those who provide block history up to the weak subjectivity point, allowing clients to start without backfilling over the P2P network

-----
<p align="center" style="display: inline-block"> 
  <a target="_blank" href="https://eth-clients.github.io/checkpoint-sync-endpoints">View the list here </a>
</p>

-----

# Contributing

If you'd like to add your endpoint to the list please read the [documentation](./CONTRIBUTING.md).
