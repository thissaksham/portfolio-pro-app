# InvestCheck | Portfolio Integrity & Verification

## The Problem: The "Dashboard vs. Reality" Gap
In the modern fintech landscape, investors rely almost exclusively on the user interfaces of their primary brokers and investment apps. This creates a significant **verification gap**: users see their holdings on a digital dashboard, but they lack a simple, independent way to confirm if those investments have actually been registered with the Asset Management Company (AMC) or the Exchange.

Recent high-profile incidents in the industry have highlighted cases where investors faced discrepancies between their app's dashboard and their actual ownership records. This "black box" effect leaves investors vulnerable to reporting errors or platform-side failures, with no easy way to "Trust but Verify" their hard-earned money.

## The Solution: InvestCheck
**InvestCheck** is a dedicated portfolio management and integrity verification tool designed to bridge this gap. It provides investors with an independent layer of truth by cross-referencing their manually tracked portfolio against official **Consolidated Account Statements (CAS)**.

By securely parsing your CAS PDF (generated from NSDL/CDSL or CAMS/KFintech), InvestCheck ensures that every unit and share you believe you own is accurately reflected in the official depository or AMC records.

## Key Features
- **🛡️ Portfolio Integrity Verification:** Securely upload your CAS PDF to verify your Mutual Fund and Stock holdings. The app uses the **CASParser API** to extract official data and compare it with your dashboard.
- **🔑 Bring Your Own Key (BYOK):** Users can provide their own CASParser API key in the settings. This allows you to bypass shared platform limits and use your own credits for statement parsing.
- **📊 Unified Dashboard:** A clean, high-performance interface to track Mutual Funds, Stocks, and Fixed Deposits in one place.
- **📈 Real-time Data:** 
  - **Mutual Funds:** Latest NAVs fetched directly via MFAPI.
  - **Stocks:** Real-time prices synced using Yahoo Finance.
- **📜 Transaction History:** Maintain a detailed log of every Buy/Sell transaction with automatic weighted average cost calculation and descending chronological view.
- **🔒 Secure & Private:** Built with Firebase Authentication and Firestore, ensuring your financial data is private and accessible only to you.
- **⚡ Serverless Architecture:** Optimized for Vercel with serverless functions handling API proxies and PDF parsing to ensure reliability and bypass CORS restrictions.

## Tech Stack
- **Frontend:** React 18, TypeScript, Tailwind CSS, Framer Motion (animations), Lucide React (icons).
- **Backend:** 
  - **Firebase:** Authentication (Google Login) and Firestore (NoSQL Database).
  - **Vercel Serverless Functions:** Node.js functions for secure API interactions.
- **APIs:**
  - **CASParser API:** For official statement parsing.
  - **MFAPI:** For Mutual Fund NAVs and search.
  - **Yahoo Finance:** For real-time stock market data.

## Environment Variables
To run this project, you will need to add the following environment variable:
- `CASPARSER_API_KEY`: The default API key used for the CAS verification feature. **Note:** Users can override this by providing their own key in the app settings (BYOK).

## Bring Your Own Key (BYOK)
InvestCheck supports a "Bring Your Own Key" model for CAS statement parsing. 
- **Privacy:** Your personal API key is stored securely in your private Firestore document, never shared with other users.
- **Limits:** Using your own key ensures you aren't affected by the shared platform's daily parsing limits.
- **Setup:** Simply click your profile photo, open **Settings**, and paste your key from [CASParser](https://app.casparser.in/).

## Firebase Configuration
This project uses **Firebase** for:
- **Authentication:** Google Login for secure user sessions.
- **Firestore Database:** Real-time storage for your portfolio and transactions.

The Firebase configuration is currently managed in `src/firebase.ts`.

## Getting Started
1. Clone the repository.
2. Install dependencies: `npm install`.
3. Start the development server: `npm run dev`.
4. Build for production: `npm run build`.

---
*InvestCheck is not a broker. It is an independent verification layer for your financial peace of mind.*
