# GX Exchange Python SDK

Official Python SDK for the GX Exchange API. Provides a complete interface for programmatic trading, account management, and real-time market data on the GX Chain network.

## What It Does

The Python SDK connects your trading systems to GX Chain's high-performance matching engine. It handles EIP-712 transaction signing, REST API calls, and WebSocket subscriptions so you can focus on strategy logic rather than protocol details.

## Quick Start

```bash
pip install gx-exchange-sdk
```

## Usage

### Place a Limit Order

```python
from gx_exchange.utils import constants
from gx_exchange import Exchange, Info

info = Info(constants.MAINNET_API_URL, skip_ws=True)
exchange = Exchange(wallet, constants.MAINNET_API_URL)

# Place a GTC limit buy for 0.2 ETH at $1100
result = exchange.order("ETH", True, 0.2, 1100, {"limit": {"tif": "Gtc"}})
print(result)
```

### Subscribe to Real-Time Market Data

```python
info = Info(constants.MAINNET_API_URL)

info.subscribe({"type": "l2Book", "coin": "ETH"}, print)
info.subscribe({"type": "trades", "coin": "BTC"}, print)
info.subscribe({"type": "allMids"}, print)
```

### Query Account State

```python
user_state = info.user_state(address)
for position in user_state["assetPositions"]:
    print(position["position"])
```

## Configuration

| Parameter | Description |
|---|---|
| `MAINNET_API_URL` | Production endpoint for GX Exchange |
| `TESTNET_API_URL` | Testnet endpoint for development |
| `wallet` | Ethereum-compatible wallet for EIP-712 signing |

## Requirements

- Python 3.9+

## Documentation

- [Python SDK Reference](https://docs.gx.exchange/for-developers/api/python-sdk)
- [API Reference](https://docs.gx.exchange/for-developers)
- [Trading Guide](https://docs.gx.exchange/trading)

## Links

- [GX Exchange GitHub](https://github.com/GX-EXCHANGE)
- [GX Exchange](https://gx.exchange)

## License

MIT
