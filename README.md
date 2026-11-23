# Friends of Solway website

The website for Friends of Solway, the parent-led fundraising committee for Solway Primary School, Masterton.

Live at **https://www.friendsofsolway.co.nz**. It is hosted free on GitHub Pages from the `main` branch of this repo. Every change saved to `main` goes live within a minute or two, so check your edits before you save them.

## How the site is put together

| Where | What it is |
|---|---|
| `index.html` | Homepage: fundraising goal, What's On, Past Fundraisers preview |
| `past-fundraisers.html` | Past Events: one card per fundraiser, with total raised and optional Facebook post |
| `sponsors.html` | Business sponsors (Gold / Silver / Bronze) |
| `plant-fair.html` | Plant Fair page (2026 fair is finished, so it now reads as a thank-you and isn't in the menu) |
| `privacy.html`, `refunds.html`, `terms.html` | Policies (required by Stripe) |
| `order-pizza/` | Friday pizza lunch ordering, plus success, cancel and "My Orders" pages |
| `order-tea-towels/` | Tea towel ordering, plus success, cancel and "My Orders" pages |
| `donate-plants/` | Plant Fair donation form (closed) |
| `_includes/nav.html` | **The top menu, shared by every page** |
| `_includes/footer.html` | **The footer (contact email, links, policies), shared by every page** |
| `images/` | Plant Fair poster and `images/sponsors/` logos |
| `Friends_of_Solway_Logo.png` | Main logo. Kept in the top folder because emails and other sites link to it. |
| `CNAME` | Connects the site to friendsofsolway.co.nz. Don't edit or delete. |
| `_config.yml` | GitHub Pages settings |

## Common jobs

**Change the menu or footer (e.g. add or remove a link, change the contact email).** Edit `_includes/nav.html` or `_includes/footer.html` once and every page updates.

**Add a page that uses the shared menu and footer.** Start the file with these two lines:

```
---
---
```

Then put `{% include nav.html %}` where the menu goes and `{% include footer.html %}` where the footer goes. To highlight a menu item, use `{% include nav.html active="past" %}` (options: `home`, `past`, `sponsors`, `pizza`, `teatowels`).

**Add a past fundraiser.** In `past-fundraisers.html`, copy an existing `past-card` block, change the emoji, title, date, total and description, and update the "Events completed" and "Total" numbers at the top. Add a matching `past-preview-card` in the Past Fundraisers section of `index.html`.

**Add a Facebook post to a past fundraiser.** On Facebook, open the post, click ⋯ → Embed, copy the code, and paste it inside a `fb-embed-wrap` block on the card (copy one from another card).

**Add a sponsor.** Upload the logo to `images/sponsors/` (no spaces in the filename) and copy an existing sponsor card in `sponsors.html`, pointing it at `/images/sponsors/YourLogo.jpg`.

**Open or close an online fundraiser.** Update its card in the What's On section of `index.html` (the `🟢 Open now` / `🔒 closed` tag and text).

**Each term: pizza delivery dates.** Update the delivery date list in `order-pizza/index.html`.

## Behind the order forms

The pizza, tea towel and plant donation forms send orders to Google Apps Scripts, which create Stripe payments and record paid orders in Google Sheets. The Apps Script web-app links are in each form's HTML. They are meant to be public; no Stripe keys or passwords are stored in this repo, and none should ever be added.

- After changing an Apps Script: Deploy → Manage deployments → pencil → New version → Deploy.
- Stripe test and live modes have separate keys, Price IDs and webhooks.

## Image tips

Keep images small so the site loads quickly on phones. Aim for under 500 KB (logos under 100 KB) and use JPG for photos and posters.
