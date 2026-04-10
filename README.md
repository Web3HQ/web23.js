# web23.js

[![npm version](https://badge.fury.io/js/web23.js.svg)](https://badge.fury.io/js/web23.js)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

The bridge between Web 2.0 and Web 3.0 for your site/app! Similar to the BlueMirror addon, but built as a comprehensive JavaScript library to seamlessly integrate blockchain functionality into traditional web applications.

## Features

- 🌉 **Easy Web2-to-Web3 Integration** - Seamless bridge between traditional web applications and blockchain networks
- ⚡ **Lightweight & Fast** - Minimal dependencies with optimal performance
- 🔐 **Secure by Default** - Built-in security best practices for crypto operations
- 🔌 **Multi-Chain Support** - Compatible with Ethereum, Polygon, and other EVM-compatible chains
- 📱 **React & Vue Compatible** - Works with modern frontend frameworks
- 🎯 **Developer-Friendly API** - Intuitive and well-documented interface

## Installation

### npm
```bash
npm install web23.js
```

### yarn
```bash
yarn add web23.js
```

### pnpm
```bash
pnpm add web23.js
```

## Quick Start

### Basic Setup

```javascript
import Web23 from 'web23.js';

// Initialize the library
const web23 = new Web23({
  chainId: 1, // Ethereum mainnet
  rpcUrl: 'https://eth.public-rpc.com'
});
```

### Connect Wallet

```javascript
// Connect to user's wallet
const wallet = await web23.connectWallet();
console.log('Connected:', wallet.address);
```

### Execute Smart Contract Interaction

```javascript
// Interact with smart contracts
const result = await web23.call({
  contract: '0x...',
  method: 'balanceOf',
  params: ['0x...']
});
```

## API Documentation

### Core Methods

#### `connectWallet()`
Establishes a connection to the user's wallet (MetaMask, WalletConnect, etc.)
- Returns: `Promise<{ address: string, balance: string }>`

#### `call(options)`
Execute a read-only smart contract call
- `options.contract` - Contract address
- `options.method` - Contract method name
- `options.params` - Method parameters
- Returns: `Promise<any>`

#### `send(options)`
Execute a transaction to modify blockchain state
- `options.contract` - Contract address
- `options.method` - Contract method name
- `options.params` - Method parameters
- `options.value` - ETH amount (optional)
- Returns: `Promise<{ hash: string, receipt: TransactionReceipt }>`

## Configuration

```javascript
const web23 = new Web23({
  chainId: 1,           // Network ID
  rpcUrl: 'https://...', // RPC endpoint
  gasMultiplier: 1.1,   // Gas fee multiplier
  timeout: 30000        // Request timeout in ms
});
```

## Supported Networks

- Ethereum (Mainnet & Testnets)
- Polygon (Matic)
- Binance Smart Chain
- Arbitrum
- Optimism
- And more EVM-compatible chains

## Examples

### React Integration

```javascript
import Web23 from 'web23.js';
import { useState } from 'react';

function App() {
  const [account, setAccount] = useState(null);
  const web23 = new Web23();

  const handleConnect = async () => {
    const wallet = await web23.connectWallet();
    setAccount(wallet.address);
  };

  return (
    <div>
      <button onClick={handleConnect}>Connect Wallet</button>
      {account && <p>Connected: {account}</p>}
    </div>
  );
}
```

## Contributing

We welcome contributions! Please see our [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Development Setup

```bash
git clone https://github.com/Web3HQ/web23.js.git
cd web23.js
npm install
npm test
npm run build
```

## Common Issues

**Q: "User rejected the request"**
- A: User declined the wallet connection. App should handle this gracefully.

**Q: High gas fees?**
- A: Consider using Layer 2 solutions like Polygon or Arbitrum for cheaper transactions.

**Q: Network errors?**
- A: Check RPC endpoint health and your internet connection.

## License

MIT © 2026 Web3HQ

## Support

- 📖 [Documentation](https://github.com/Web3HQ/web23.js/wiki)
- 💬 [Discussions](https://github.com/Web3HQ/web23.js/discussions)
- 🐛 [Report Issues](https://github.com/Web3HQ/web23.js/issues)

---

**Built with ❤️ to bridge Web 2.0 and Web 3.0**
