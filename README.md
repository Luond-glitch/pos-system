# Universal POS: client

## Run it (macOS, in Terminal)
    cd universal-pos
    npx serve client          # needs Node.js; or without Node:
    python3 -m http.server 8080 --directory client
Open the address it prints (http://localhost:3000 or http://localhost:8080). The start page has two doors.

## Pages
- index.html: start page. "I'm a client" goes to shop.html, "Staff and managers" goes to login.html.
- shop.html: client page. Sign up / sign in, browse products with images, see own receipts.
- login.html: staff sign in. Managers see everything, cashiers see Dashboard and Checkout only.
- Manager pages: Sales (refunds), Products (with images), Inventory, Purchases, Reports, Clients, Staff.

Staff demo logins: manager@shop.co.ke / manager123, cashier@shop.co.ke / cashier123.
Clients create their own account. At the till, add the client by phone or email so purchases appear on their page.
Demo data lives in the browser's localStorage. Reset: DevTools Console `localStorage.clear()`, then reload.

## Connecting the backend
Set `CONFIG.USE_MOCK = false` in `client/js/api.js`. Pages only call `API.*`; `RealAPI` lists the endpoints expected.
Backend must: hash passwords, enforce roles and the 5% cashier discount limit, store product images in file storage (the mock keeps small JPEG data URLs), and serve /public/products without cost or stock counts.
