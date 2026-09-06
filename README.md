# BedBox Hostels — Supabase Simple Setup

A simplified Supabase version for a **150-bed hostel** with **2 admins + 1 warden**.

## You only need to do this once

### Step 1 — Create Supabase
Create a project at Supabase.

### Step 2 — Create the database
In Supabase Dashboard open **SQL Editor → New query**.
Open `supabase/schema.sql` from this ZIP, copy everything, paste it, and click **Run**.

### Step 3 — Create your first login
Go to **Authentication → Users → Add user**.
Create the main admin email + password.

### Step 4 — Make yourself Admin
Open BedBox, click **⚙ Setup Supabase**, paste:
- **Project URL**: Dashboard → Project Settings → API → Project URL
- **Publishable key** (or legacy anon key): Dashboard → Project Settings → API

Click **Save & Connect**, then sign in.

If this is the first account, BedBox can make the signed-in user the first Admin using the protected **Make me first Admin** action in the setup flow.

### Step 5 — Add the other two staff accounts
Create the second admin and warden under **Authentication → Users**.
An admin can then assign their role from **Staff**.

## What goes in the browser
Only the Supabase **publishable/anon** key. Never use a `service_role` or `sb_secret_` key in this website.

## Hosting
The website is static and can be hosted on GitHub Pages, Netlify, Vercel, Cloudflare Pages, or another HTTPS static host.

## Important
- The database is protected with Supabase Row Level Security (RLS).
- Bed allocation is atomic, so two staff members cannot take the same bed at the same time.
- Keep administrator MFA enabled for production.
- For production email/password recovery and verification emails, configure a custom SMTP provider in Supabase.

## Local test
Run an HTTP server from the project folder, for example:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.
