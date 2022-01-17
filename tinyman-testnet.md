# Tinyman Testnet

Tinyman has launched on Algorand Mainnet ([app.tinyman.org](https://app.tinyman.org)) but Testnet is still available try things out without risks!

The contracts have been deployed to Algorand Testnet and the user interface is available at [https://testnet.tinyman.org](https://testnet.tinyman.org). This interface allows users to try out the UI and do pooling and swapping operations using Testnet assets (Algo & ASAs with no real world value).&#x20;

Please be aware that some features may appear on the testnet version before they are fully tested and complete.&#x20;

We do welcome feedback from all users of Tinyman Testnet/Mainnet so please let us know your thoughts and feelings on Discord or Telegram.

## Getting Started

_Some of these steps may not be necessary if you have previously used Algorand Testnet._

1. Create/import an Algorand account to [MyAlgo](https://wallet.myalgo.com) wallet.
2. Switch the MyAlgoWallet UI from Mainnet to Testnet in the top right corner.
3. Check your Algo balance and if necessary add some Testnet Algo to your account from [https://dispenser.testnet.aws.algodev.network/](https://dispenser.testnet.aws.algodev.network)
4. Opt-In to the Tiny USDC asset by clicking **Add Asset** ![](<.gitbook/assets/Screenshot 2021-08-06 at 16.56.05.png>)&#x20;
5. Enter the ID 21582668 and sign the transaction.
6. Within a minute you will receive some Tiny USDC in your account. You are welcome.
7. Go to [https://testnet.tinyman.org](https://testnet.tinyman.org) and click **Connect to a Wallet**.
8. Watch out for blocked popups in the browser. You may need to allow popups from wallet.myalgo.com.
9. Now you can use the UI to swap your hard earned Tiny USDC or Algo for the other available assets.

## Testnet FAQ

### What about using other wallets?

We will be introducing other wallet options soon but the integrations are currently still in development so rather than frustrate you with them we have disabled them until they are ready.

### Why Tiny USDC?

We created the Tiny USDC ASA to have an ASA on Testnet that everyone can easily get their hands on. It is intended to mimic the USDC stable coin. In theory you could just start off with Algo and swap into other ASAs on Tinyman but unfortunately the supply of Algo is relatively limited on Testnet so each account can only receive a small amount at a time. As we created this ASA we control the full supply and so can provide much larger amounts without causing problems for the larger Algorand Testnet network.

If you wish to create new pools with other ASAs we encourage you to create a `TinyUSDC - Your ASA` pool too so that everyone has a way of swapping through the pools.

### What are the other Tiny\* ASAs?

We have also created Tiny USDt and Tiny Gold (so far) modeled on Mainnet assets to have a variety of assets available with various differences. Tiny Gold has 5 decimal places unlike the majority of assets which use 6. Tiny USDt should be roughly equivalent to Tiny USDC so that pool might be fun. It also is unusual in that it has a lower case letter in its Unit Name. We may add more assets to our collection as we find more test scenarios to reproduce.

### I love Tinyman so much I'm gonna HODL these even though this is Testnet!!!

A: Sure, ok. You do you.\
B: We might take them back. Yeah. We reserve the right to do that if we somehow run out of our 2^64 supply and need them for something more worthwhile.\
C: That's not a question.&#x20;

### I found a UI/UX issue. What should I do?

That's great. That's what Testnet is for. Please let us know in Discord/Telegram with as much detail as possible. Include screenshots/recordings if it helps.&#x20;

### I think I found a contract vulnerability! What should I do?

That's not so great. Please DO NOT exploit the vulnerbility on testnet if possible. Please test it on a private network where the transactions will not be seen by others.

Please email us at security@tinyman.org with the details of any possible vulnerability you find with specific references to the source code. DO NOT use this email for UI issues.

### Where are the contracts?

For technical users wishing to create an integration or examine the transactions:\
The stateful [Validator App](design-doc.md#docs-internal-guid-b18fd459-7fff-aa47-087b-2bcfdededbc5) Id is currently [62368684](https://testnet.algoexplorer.io/application/62368684).\
See [Contracts](contracts.md) for more details including links to the annotated source and audits.
