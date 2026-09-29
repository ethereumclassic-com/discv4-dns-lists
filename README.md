# Ethereum Classic DNS discovery lists

Signed lists of Ethereum Classic and Mordor nodes, published in DNS so that
clients find their first peers through
[EIP-1459](https://eips.ethereum.org/EIPS/eip-1459) discovery. The lists are
rebuilt every night from a crawl of the discv4 network, and every published list
is committed to this repository, so the record of what clients were given is
public. They are maintained in the
[`ethereumclassic`](https://github.com/ethereumclassic) organization by its core
developers and community contributors.

> [!IMPORTANT]
> **Move to the community-maintained trees.** Core-geth `v1.12.x` finds its first
> peers through endpoints the ETC Cooperative maintained: DNS trees published from
> [`etclabscore/discv4-dns-lists`](https://github.com/etclabscore/discv4-dns-lists)
> and, in its later releases, the Cooperative's bootnodes. The Cooperative entered
> maintenance mode at the end of 2024, and its board has communicated that it will
> dissolve by the end of 2026 and that those trees will be archived as it does.
> The trees published here continue that service. Core-geth
> [`v1.13.x`](https://github.com/ethereumclassic/core-geth/releases/latest), from
> [`ethereumclassic/core-geth`](https://github.com/ethereumclassic/core-geth),
> reads them by default, and a `v1.12.x` node can switch with
> [one flag](#quick-start).
> [The ETC Cooperative transition](https://docs.coregeth.com/etc-cooperative-transition/)
> lists where the Cooperative's other services continue.

## The trees

```
enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.classic.ethereumclassic.net
enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.classic.ethclassic.net
enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.classic.ethereumclassic.network
enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.mordor.ethereumclassic.net
enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.mordor.ethclassic.net
enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.mordor.ethereumclassic.network
```

`all.classic.` is Ethereum Classic and `all.mordor.` is its Mordor test network.
All six are signed by one key, the text between `enrtree://` and `@`, and the
same URLs are compiled into core-geth. Each directory in this repository holds
one published tree and is named after the DNS name it serves.

## Quick start

**Core-geth `v1.13.x`:** nothing to configure. Both networks read these trees by
default.

**Core-geth `v1.12.x`:** add `--discovery.dns` with the three trees for your
network.

```sh
geth --classic --discovery.dns "enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.classic.ethereumclassic.net,enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.classic.ethclassic.net,enrtree://APDLRZ2T7ERXPWXX4D5USB32NIFYHXMFVZQ3DZALK6JJJ5L4VSYIQ@all.classic.ethereumclassic.network"
```

[Using the trees](docs/using-the-trees.md) has the Mordor and config-file forms.

## Documentation

| Page | What it covers |
|---|---|
| [Using the trees](docs/using-the-trees.md) | Pointing any core-geth release at these trees |
| [Verifying a tree](docs/verifying-a-tree.md) | Checking what DNS serves against what this repository recorded |
| [DNS hosting and outages](docs/dns-outage.md) | What a DNS outage affects, and starting a node without the trees |
| [How nodes are chosen](docs/node-selection.md) | What gets a node listed, the current fork ID, and tree size |
| [How the lists are built](docs/pipeline.md) | The nightly pipeline, its safety checks, and running it by hand |
| [Why this repository exists](docs/history.md) | The ETC Cooperative transition and the predecessor trees |

## Status

Every scheduled run reports its result on one issue labeled
[`pipeline-status`](https://github.com/ethereumclassic/discv4-dns-lists/issues?q=label%3Apipeline-status).
Subscribe to it to be notified when a run fails and when it recovers.

## Support this work

Publishing these trees has been unfunded public-goods work. Mining pools,
exchanges, block explorers, RPC providers and anyone running an Ethereum Classic
node depend on peer discovery working every night. If your operation relies on
Ethereum Classic, please help fund that work.
[Support this work](docs/support.md) carries the routes: an invoiced maintenance
agreement for organizations, or a direct transfer to an address provided on
request.

## License

MIT. See [LICENSE](LICENSE).
