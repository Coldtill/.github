# Self-hosted crypto payment gateway - ColdTill

**Self-hosted crypto payments. 200+ coins on 35+ chains, straight to your own cold wallet.**

No sign-up, no KYC or KYB, and no approval queue. You run Coldtill on your own Linux server. Customers pay addresses that can only send to the wallet you set, so breaking into the server can't redirect the money. There's no processor balance and no account anyone can freeze.

[Website](https://coldtill.com) · [Docs](https://coldtill.com/docs/) · [Live demo](https://demo.coldtill.com/) · [Download](https://coldtill.com/download/) · [Pricing](https://coldtill.com/pricing/) · [Compare](https://coldtill.com/compare/)

![The Coldtill dashboard: confirmed volume, deposits by asset and recent payments](https://coldtill.com/img/dashboard-overview.webp)

## Install the free edition

No account. Ubuntu, Debian or Linux Mint, with Docker. A server with 2 vCPU and 4 GB of memory is plenty.

```bash
curl -fsSL https://coldtill.com/install.sh | sudo bash -s -- --edition free
```

The script downloads the latest release, checks its SHA-256, generates your secrets and starts Coldtill. Run it again to upgrade.

[Releases and checksums](https://github.com/Coldtill/self-hosted-crypto-payment-gateway/releases/latest) · [Self-hosting guide](https://coldtill.com/docs/self-hosting/) · [What the 2% fee means](https://coldtill.com/download/#fee)

## What you get

- **200+ coins.** Ethereum, Base, Polygon, BNB Chain, Tron, Solana and Bitcoin directly, including USDT and USDC. XRP, TON, Sui, Cardano, Zcash and more through auto-convert, settled to you as USDC or USDT.
- **Your cold wallet, fixed on chain.** On Ethereum-style chains, Tron and Solana, every deposit address is a contract that can only pay your cold wallet. Bitcoin addresses come from your own wallet's public key.
- **No one to switch you off.** No licence server and no kill switch. Coldtill keeps taking payments if coldtill.com goes offline.
- **A checkout on your domain.** QR codes, exact amounts, live confirmation progress and your branding, such as `pay.yourshop.com`.
- **Sweeps and payouts.** Funds move to your cold wallet when the value justifies the gas. Refunds go out from a small hot wallet, with an address book, limits and two-factor approval.
- **Many shops, one server.** Each project has its own wallets, API keys, webhooks and checkout domain.

## Pricing

The editions are the same software, with unlimited projects and servers for your own business. They differ only in the fee taken when funds are swept to your cold wallet. Bitcoin and auto-converted payments carry no fee on any edition.

| | Free | Standard | Pro |
| --- | --- | --- | --- |
| Price | $0 | $499 once | $999 once |
| Fee on sweeps | 2% | 1% | None |
| Get it | [This repo](https://github.com/Coldtill/self-hosted-crypto-payment-gateway), no account | [Buy](https://coldtill.com/pricing/) | [Buy](https://coldtill.com/pricing/) |

The rate is fixed in each deposit wallet when you create it, and it can't be raised later. [Work out what's cheapest for you](https://coldtill.com/pricing/#calculator).

## For developers and agents

Create a payment with your project's API key. The response includes the checkout URL.

```bash
curl -X POST https://pay.example.com/api/v1/payment \
  -H "API-Key: $COLDTILL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"customerID":"42","amountInUSD":25.00}'
```

Webhooks are HMAC-signed and include a timestamp, so a captured request can't be replayed. The docs are written for people and for coding agents:

- [API reference](https://coldtill.com/docs/api/) and the [OpenAPI 3.1 spec](https://coldtill.com/openapi.yaml)
- [llms.txt](https://coldtill.com/llms.txt), an index of every docs page, and [llms-full.txt](https://coldtill.com/llms-full.txt), every page in one file
- [WooCommerce plugin](https://github.com/Coldtill/woocommerce-crypto-payment-gateway), MIT licensed

## Questions

**Is it custodial?** No. Customers pay addresses that only send to your cold wallet, and Coldtill runs on your server. We never see your keys, your customers or your payments.

**Do I need to pass KYB?** No. There's no application and no approval queue. Buying Standard or Pro only needs an email address and a crypto payment. You're responsible for the laws that apply where you sell.

**Which coins?** USDT, USDC, ETH, SOL, TRX, BNB and BTC directly, plus 200+ tokens on 35+ chains through auto-convert, which pays you in USDC or USDT. Auto-convert is on every edition and off by default.

**What does the fee apply to?** Sweeps on Ethereum-style chains, Tron and Solana. Bitcoin goes to your own wallet, and auto-converted payments are delivered straight to your cold wallet, so neither carries a fee.

**What if coldtill.com goes offline?** Your server keeps taking payments. The only call home is a daily update check, and you can turn it off.

Report vulnerabilities privately to security@coldtill.com. Security fixes are free for every edition. The Free edition is free to download and run; the gateway's source code isn't published.
