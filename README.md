# Learnly - Online Courses (React)

Front-end React project (Vite + react-icons).

## Run
```
npm install
npm run dev
```
Build: `npm run build`

## Features
- 12 courses with offers (offer % is calculated from MRP and price), search, category + level filters, sorting
- Random options: "Surprise Me", "Deal of the Day" shuffle, Random sort
- More options while buying: add-ons (certificate, mentor, project review, lifetime access) and coupon codes (LEARN10, NEWUSER20, FLAT100)
- Wishlist, dark/light theme, My Learning page (all saved in localStorage)
- Online compiler: JavaScript (Web Worker), Python (Pyodide, needs internet first time), HTML/CSS live preview
- PhonePe / UPI payment: opens PhonePe with amount filled, or scan the UPI QR
- PayPal payment: PayPal Buttons (PayPal balance / card), price converted INR -> USD

## Payment setup
Edit `src/config.js` and put your own UPI ID. Payment here is a demo (the user types the UTR).
For real automatic verification you must use the PhonePe Payment Gateway with a backend server.

## PayPal setup
Edit `src/config.js`:
- `PAYPAL_CLIENT_ID`: "test" works for a demo. Use your own Client ID from developer.paypal.com (Sandbox while testing, Live for real money).
- `INR_PER_USD`: set the current exchange rate.
The payment is captured in the browser. For real money, verify the order on a backend server before giving access.

## Razorpay setup
1. Create an account at razorpay.com and open Dashboard -> Account & Settings -> API Keys -> Generate Key.
2. Put the **Key ID** (rzp_test_... for testing) in `src/config.js` as `RAZORPAY_KEY_ID`.
3. Never put the Key Secret in this project. For real money, create orders and verify the payment signature on a backend server.

## Course player (new)
My Learning -> Start Learning opens the player for an enrolled course:
1. 5 videos per course. Skipping ahead is blocked; the next video unlocks only after the current one is watched fully.
2. After all 5 videos, Interview Preparation unlocks (5 MCQs, pass mark 3/5, retry allowed).
3. After passing, a Certificate PDF can be downloaded (generated in the browser, no extra library).
Progress is saved in localStorage (`learnly-progress`).
Videos are YouTube links. Edit `youtubeByCategory` / `youtubeByCourse` in `src/data.js` (link or video ID).
