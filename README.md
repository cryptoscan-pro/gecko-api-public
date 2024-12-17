# Gecko API - Cryptoscan

A TypeScript-based tool for loading and monitoring cryptocurrency pool data from GeckoTerminal API with WebSocket support.

**Contacts**: [https://t.me/dan_cryptoscan](https://t.me/dan_cryptoscan)

What you get:

- Free setup into your hosting
- Free help to integrate app to your server
- Full access to the codebase and code updates
- Free updates for app, you can request for free updates via access to issues
- Full access to Project Time tracking by developers

## Features

- Fetch and monitor cryptocurrency pools across multiple networks
- Real-time WebSocket updates for pool data
- Liquidity-based prioritization system
- Rate limiting and request throttling
- CEX token price monitoring
- Persistent data storage using FileMap

## Installation

```bash
# Clone the repository
git clone https://github.com/cryptoscan-pro/gecko-api.git

# Install dependencies
npm install
```

## Configuration

Create a `.env` file with the following variables:
```env
GECKO_CONCURRENCY=1  # Number of concurrent requests
```

## Usage

### Starting the Service
```bash
npm start
```

### Main Components

#### Pool Loading
- `loadPools()`: Loads pool data based on liquidity groups
- `searchPools()`: Search for specific pools by symbol
- `fetchPools()`: Fetches pool data from GeckoTerminal API

#### CEX Integration
- `getCexCoins()`: Retrieves coins listed on centralized exchanges
- `fetchCexTokens()`: Fetches token data from CEX API

### Liquidity Groups

Pools are categorized into four liquidity groups:
- ULTRA_LOW: < $100
- LOW: $100 - $100,000
- MEDIUM: $100,000 - $1,000,000
- HIGH: > $1,000,000

Each group has different update intervals and priorities for data fetching.

### WebSocket Support

The service includes a WebSocket server for real-time data broadcasting. Clients can connect to receive updates based on configurable thresholds.

## API Reference

### Pool Interface
```typescript
interface Pool {
    base: string;
    quote: string;
    network: string;
    poolAddress: string;
    address: string;
    priceUSD: number;
    createdAt: number;
    fdvUSD: number;
    marketCapUSD: number;
    // ... (includes various time-based metrics)
}
```

### Rate Limiting

The service implements rate limiting with:
- 30 requests per minute (RPM)
- Configurable concurrency via environment variables
- Automatic retry mechanism for failed requests

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

ISC License
