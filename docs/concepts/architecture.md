# Architecture

Web3aggregator routes requests across a tiered infrastructure that
prioritizes reliability and low latency.

## Components

| Layer | Role |
|---|---|
| **Edge** | Geographically distributed ingress points handling TLS termination and request routing |
| **Aggregation** | Routes RPC and read requests to the best available upstream provider per region |
| **State Cache** | Aggregates on-chain state for high-cardinality reads, refreshed continuously |
| **Stream Layer** | Real-time event delivery over persistent WebSocket connections |

## Request flow

1. Client opens connection to nearest **Edge** region.
2. Request is authenticated and authorized at the edge.
3. **Aggregation** layer selects an upstream provider based on
   health, latency, and method support.
4. Response is returned to the client. Aggregated reads may be
   served from the **State Cache** without contacting an upstream.

## Regional coverage

Web3aggregator operates ingress points across multiple regions to
keep client latency low. See the [Status Page](https://status.web3aggregator.io)
for the current set of active regions.
