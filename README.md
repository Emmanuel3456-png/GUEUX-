# GUEUX — AI Fashion OS

Upload Ankara / Aso Oke rag photo → Get 10 luxury drip designs + auto fashion store.

## Prices (Naira only)

| Plan    | Price     | What you get                          |
|---------|-----------|---------------------------------------|
| Free    | ₦0        | 2 free design generations (trial)     |
| Starter | ₦15,000   | 50 designs/mo, 3 stores, .com.ng      |
| Pro     | ₦60,000   | Unlimited designs, 10 stores, .com    |
| Empire  | ₦300,000  | Everything + white-label + API        |

## How to Publish (so it opens)

The app **does not open** when you tap the HTML file on your phone.  
It must be hosted on the internet.

### Easiest way: Vercel + GitHub

1. Create a GitHub repository.
2. Upload these files:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-144.png`
   - `icon-192.png`
   - `icon-512.png`
3. Go to [vercel.com](https://vercel.com) → Import the GitHub repo → Deploy.
4. Open the Vercel link on your phone. It will work.

### Using Termux to update later

```bash
cd ~/gueux
# edit index.html (or pull changes)
git add .
git commit -m "Update"
git push
```
Vercel will auto-redeploy.

## Connect Selar for Payment

1. Create 3 products on Selar with the prices above.
2. Copy each product link.
3. Open `index.html` and find this section near the top:

```js
const SELAR = {
  Starter: "https://selar.com/YOUR-STARTER-PRODUCT?add_to_cart=1",
  Pro: "https://selar.com/YOUR-PRO-PRODUCT?add_to_cart=1",
  Empire: "https://selar.com/YOUR-EMPIRE-PRODUCT?add_to_cart=1"
};
```

Replace the three links with your real Selar product links (keep `?add_to_cart=1`).

4. In each Selar product settings, turn on **Redirect after purchase** and set the URL to:

```
https://YOUR-VERCEL-URL.vercel.app/?paid=1
```

After a customer pays on Selar, they are sent back and the app unlocks automatically.

## Free Trial
Users can generate designs 2 times for free. After that they must pay via Selar.
