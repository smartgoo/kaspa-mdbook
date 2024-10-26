# Testing

Given that Python SDK is new and under active development, it should be used for testing and non-production use cases.

## Detailed Examples

Below are a handful of simple examples. More detailed example usage can be found in the Kaspa `python` crate at [https://github.com/aspectron/rusty-kaspa/tree/python/python/examples](https://github.com/aspectron/rusty-kaspa/tree/python/python/examples).

## Simple Examples

### RPC Request
```python
import asyncio
from kapsa import Resolver, RpcClient

async def main():
    # Using Resolver to connect to Kaspa PNN
    resolver = Resolver()
    client = RpcClient(resolver)
    await client.connect()

    print(await client.get_server_info())

if __name__ == "__main__":
    asyncio.run(main())
```

### RPC Subscription
```python
import asyncio
from kaspa import Resolver, RpcClient

def handle_block_added_event(event, name, **kwargs):
    print(f"{name} | {event}")

def handle_vcc_event(event, name, **kwargs):
    print(f"{name} | {event}")

async def main():
    # Use Resolver to connect to Kaspa PNN
    resolver = Resolver()
    client = RpcClient(resolver)
    await client.connect()

    # Add event listeners and subscribe
    client.add_event_listener("block-added", callback=handle_block_added_event, name="block-handler")
    client.add_event_listener("virtual-chain-changed", callback=handle_vcc_event, name="vcc-handler")
    await client.subscribe_block_added()
    await client.subscribe_virtual_chain_changed(True)

    await asyncio.sleep(5)

    await client.unsubscribe_block_added()
    await client.unsubscribe_virtual_chain_changed(True)

    await client.disconnect()

if __name__ == "__main__":
    asyncio.run(main())
```

### Mnemonic generation: 
```python
from kaspa import Mnemonic

if __name__ == "__main__":
    # Random mnemonic
    mnemonic1 = Mnemonic.random()

    # mnemonic from phrase
    mnemonic2 = Mnemonic(phrase=mnemonic1.phrase)
```