# Azen Store — Billing & Inventory Management

A clean, responsive, admin-only billing and stock management web app. Currency: PKR (Rs.).

## Included
- Admin email/password login through Supabase Auth
- Dashboard, products and product image uploads
- Stock purchases and stock-on-hand updates
- Billing, invoice printing, discounts, payment receiving and customer balances
- Sales returns (return quantity is added back to stock)
- Expenses, basic reports and sales CSV export
- JSON backup download and restore
- Responsive desktop/mobile layout

## Technology
- Vite + vanilla JavaScript
- Supabase Database, Authentication and Storage
- Deployable to Vercel or Netlify

## 1. Create Supabase project
1. Create a project at https://supabase.com/
2. Open SQL Editor and run `supabase/schema.sql`.
3. Go to Authentication > Users > Add user. Create your admin email and password.
4. In Project Settings > API, copy Project URL and anon/public key.
5. Open `src/main.js`; replace `YOUR_SUPABASE_URL` and `YOUR_SUPABASE_ANON_KEY`.

Never put the Supabase `service_role` key in frontend code.

## 2. Run locally
Install Node.js (LTS), then in this folder run:
```bash
npm install
npm run dev
```
Open the local URL printed by Vite.

## 3. Deploy with GitHub + Vercel
1. Push this folder to a GitHub repository.
2. Sign in at https://vercel.com/ and import the repository.
3. Framework preset: Vite. Build command: `npm run build`. Output directory: `dist`.
4. Deploy. Vercel gives you a live URL.
5. In Supabase > Authentication > URL Configuration, add your Vercel URL to Site URL and Redirect URLs.

## Important operating notes
- This is a functional first release, not an audited accounting/ERP product.
- Create regular JSON backups and keep a copy outside the hosting account.
- Test billing, stock, returns and restore with sample records before live business use.
- Returns currently add returned quantity back into stock; exchange workflow should be completed by recording the replacement sale separately.
- Backup includes database records and image URLs, not the original image binary files. Product images remain in Supabase Storage.
- For production hardening, use database transactions/RPC for atomic invoice + stock updates, add audit logs, invoice numbering controls and stricter per-admin authorization. The SQL policies allow authenticated users; keep only your intended admin user in Supabase Auth.
