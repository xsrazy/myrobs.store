# MyRobs.Store

MyRobs.Store is a single-page online store that sells Roblox follower packages. A customer picks a package (or enters a custom amount), fills in one order form, and pays by QRIS. The store runs at [myrobs.store](https://myrobs.store) under the tagline "Trusted Roblox Followers Service".

> This repository is documentation only. The store's source code is private; this README describes what the site is, why it exists, and how it works.

## Why This Exists

Buying followers for a Roblox account usually happens through chat with a seller: agree on a price in DMs, transfer money manually, then wait and hope. That process is slow, error-prone, and has no paper trail for either side. MyRobs.Store was built to turn that informal transaction into a normal e-commerce checkout: fixed published prices, a structured order form, a standard QRIS payment, and an order record that both sides can point to.

## Purpose

- Sell Roblox follower packages at fixed, published prices in Indonesian Rupiah.
- Collect every order through one structured form (package, Roblox username, profile link, buyer name, and email) instead of free-form chat.
- Accept payment through QRIS so anyone with an Indonesian e-wallet or mobile banking app can pay by scanning one code.
- Give the seller a clean queue of paid orders to process, instead of screenshots in a chat thread.

## Features

- **Fixed packages:** 10,000 followers for IDR 250,000; 20,000 for IDR 450,000; 30,000 for IDR 650,000; 40,000 for IDR 750,000; and 50,000 for IDR 1,000,000.
- **Custom amounts:** any follower count from a minimum of 10,000, priced at IDR 25 per follower.
- **Live total:** the order total updates automatically as the package or custom amount changes.
- **One-form checkout:** package, Roblox username, Roblox profile link, full name, email address, payment method, and optional notes, all on one page.
- **QRIS payment:** one QR code payable from DANA, OVO, GoPay, ShopeePay, or any mobile banking app.
- **Server-confirmed orders:** an order is only processed after the payment is confirmed by the payment gateway, not when the buyer clicks the pay button.

## Frontend

The whole storefront is a single page with a single job: the order form. Visitors see the package list as selectable options, with the 10,000-follower package selected by default. Choosing "Custom" reveals an extra field for the desired follower amount. A summary box shows the current total price, and the form ends with a "Proceed to Payment" button. There are no separate catalog, FAQ, or checkout pages; everything happens in that one view.

## Backend / How It Works

- The site is a Next.js application hosted on Vercel.
- When an order is submitted, the server recalculates the price from the selected package or custom amount, so the amount charged always matches the published rates regardless of what the browser sent.
- The order is stored in a database, and the buyer is given a QRIS code issued by the payment gateway.
- The gateway notifies the server through a signed webhook when a payment settles. Only then is the order marked paid and queued for fulfillment; unpaid or unconfirmed orders are never processed.
- Confirmation and fulfillment messages to the buyer are tied to that verified payment status, so the store never has to trust a buyer's claim that they already paid.

## Summary

MyRobs.Store is a focused one-page store: fixed follower packages plus a custom option at IDR 25 per follower, one structured order form, QRIS-only payment, and a backend that prices and confirms every order on the server before anything is processed.

## 🌐 Socials
[![Behance](https://img.shields.io/badge/Behance-1769ff?logo=behance&logoColor=white)](https://behance.net/xsrazy) [![Discord](https://img.shields.io/badge/Discord-%237289DA.svg?logo=discord&logoColor=white)](https://discord.gg/xsrazy) [![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?logo=Facebook&logoColor=white)](https://facebook.com/xsrazy) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/xsrazy) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/xsrazy) [![Medium](https://img.shields.io/badge/Medium-12100E?logo=medium&logoColor=white)](https://medium.com/@xsrazy) [![Pinterest](https://img.shields.io/badge/Pinterest-%23E60023.svg?logo=Pinterest&logoColor=white)](https://pinterest.com/xsrazy) [![Quora](https://img.shields.io/badge/Quora-%23B92B27.svg?logo=Quora&logoColor=white)](https://quora.com/profile/xsrazy) [![Reddit](https://img.shields.io/badge/Reddit-%23FF4500.svg?logo=Reddit&logoColor=white)](https://reddit.com/user/xsrazy) [![Stack Overflow](https://img.shields.io/badge/-Stackoverflow-FE7A16?logo=stack-overflow&logoColor=white)](https://stackoverflow.com/users/31065073) [![Twitch](https://img.shields.io/badge/Twitch-%239146FF.svg?logo=Twitch&logoColor=white)](https://twitch.tv/xsrazy) [![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?logo=Twitter&logoColor=white)](https://twitter.com/xsrazy) [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/c/xsrazy)

## 💰 You can help me by Donating
[![BuyMeACoffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?style=plastic&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/xsrazy) [![PayPal](https://img.shields.io/badge/PayPal-00457C?style=plastic&logo=paypal&logoColor=white)](https://paypal.me/xsrazy) [![Patreon](https://img.shields.io/badge/Patreon-F96854?style=plastic&logo=patreon&logoColor=white)](https://patreon.com/Xsrazy) [![Ko-Fi](https://img.shields.io/badge/Ko--fi-F16061?style=plastic&logo=ko-fi&logoColor=white)](https://ko-fi.com/xsrazy)

## License

MIT License. See [LICENSE](LICENSE) for details.
