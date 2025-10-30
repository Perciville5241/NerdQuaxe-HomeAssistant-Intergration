# NerdAxe Bitcoin Miner - Home Assistant Integration
Thanks for checking this project out, 

Home Assistant packages and Lovelace cards for monitoring NerdAxe Bitcoin miners and tracking wallet balances.

## What's Included

**Packages:**
- `nerdaxe_miner.yaml` - Monitor your NerdAxe miner hardware
- `BitcoinWallet.yaml` - Track Bitcoin mining payouts and price

**Lovelace Cards:**
- `BitcoinLoveLace` - Bitcoin wallet stats card
- `lovelaceCard2` - NerdAxe mining stats card
- `LoveLaceCard1` - Main miner monitoring card
- `LoveLaceCard3` - Additional NerdAxe configuration card
- `LoveLaceCard4` - Extra monitoring card
- `HistoryGraphCard1` - NerdAxe performance graphs

**Markdown Content:**
- `LoveLaceBitCoinStats` - Bitcoin wallet stats display

## Requirements

- Home Assistant with packages enabled
- NerdAxe miner on your local network
- Bitcoin wallet address for tracking payouts


## Installation

### 1. Enable Packages

Add to your `configuration.yaml`:
```yaml
homeassistant:
  packages: !include_dir_named packages
```

### 2. Install Package Files

Create a `packages` folder in your config directory if you haven't got one, then copy:
- `nerdaxe_miner.yaml`
- `BitcoinWallet.yaml`

### 3. Configure the Packages

**For `nerdaxe_miner.yaml`:**
- Line 14: Your miner's IP address
- Line 60: Your Bitcoin wallet address
- Lines 232, 261, 279: Uncomment and add your mobile device name for notifications

**For `BitcoinWallet.yaml`:**
- Line 10: Your Bitcoin wallet address

### 4. Add Lovelace Cards

Copy the card configurations into your Lovelace dashboard. You can add them through the UI:
1. Edit Dashboard
2. Add Card
3. Manual Card
4. Paste the YAML from the card files

### 5. Restart Home Assistant

## What You Get

### Miner Monitoring
- Real-time hash rate (GH/s)
- Chip temperature with warnings
- Pool connection status
- Share acceptance/rejection rates
- Power consumption
- Fan speed (RPM and percentage)
- Uptime tracking
- Worker name
- Wallet address validation

### Wallet Tracking
- Total BTC received from mining
- Transaction count
- Mining earnings in GBP and USD
- Live BTC price tracking
- New transaction notifications
- Price change alerts (>5% movement)

### Dashboard Cards
- Complete miner status overview
- Bitcoin wallet statistics
- Performance history graphs
- Mining stats display

## Alerts

The packages include automated notifications:

**Critical:**
- Wrong wallet address detected (30 second delay)
- Miner offline for 2+ minutes
- High temperature (>80°C)

**Informational:**
- Miner back online
- New Bitcoin transactions
- Daily mining summary (20:00)
- BTC price changes >5%

All notifications appear in Home Assistant's persistent notification panel. Uncomment the mobile app sections in the automation files for push notifications.

## Lovelace Card Examples

### Main Miner Card
Shows online status, hash rate, temperature, power, shares, and wallet validation.

### Bitcoin Wallet Card
Displays total BTC received, current value in GBP/USD, transaction count, and live price.

### History Graph Card
Tracks miner performance over time including hash rate, temperature, and power consumption.

## Troubleshooting

**Miner shows offline:**
- Check the IP address in the configuration
- Verify miner is powered on and connected to network
- Try accessing the miner's web interface directly at http://YOUR_MINER_IP

**Wallet validation fails:**
- Ensure expected wallet address matches miner configuration
- Check miner is connected to pool and mining

**Bitcoin wallet sensors unavailable:**
- Verify wallet address is correct
- blockchain.info API may be temporarily down
- Check Home Assistant logs for specific errors

**No price data:**
- Coinbase API may be temporarily unavailable
- Check internet connection
- Price updates every 15 minutes, give it time

**Lovelace cards not displaying:**
- Ensure all required sensors are available
- Check for YAML syntax errors in card configuration
- Verify packages are loaded (check Settings > System > Logs)

## Technical Details

- Miner API polled every 30 seconds
- Wallet balance updated every hour
- Bitcoin price updated every 15 minutes
- All temperatures in Celsius
- Price alerts only trigger on >5% changes
- Temperature warnings at 80°C, cleared at 70°C



## Files Overview

| File | Purpose |
|------|---------|
| `nerdaxe_miner.yaml` | Main miner monitoring package |
| `BitcoinWallet.yaml` | Bitcoin wallet tracking package |
| `BitcoinLoveLace` | Bitcoin wallet stats card config |
| `lovelaceCard2` | NerdAxe mining stats card |
| `LoveLaceCard1` | Main miner monitoring card |
| `LoveLaceCard3` | Additional NerdAxe card |
| `LoveLaceCard4` | Extra monitoring card |
| `HistoryGraphCard1` | Performance history graphs |
| `LoveLaceBitCoinStats` | Markdown content for wallet stats |

Happy to take Donations :) - Perciville
"3KVsNviwpxqziUkwkSdhmWzTT5HZFeFtpm"

## Support

If you're having issues, check the Home Assistant logs first:
Settings > System > Logs

For miner-specific problems, check the NerdAxe documentation and community forums.
