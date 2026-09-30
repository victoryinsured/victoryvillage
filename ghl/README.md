# Victory Village pages for GoHighLevel

| File | Page | Suggested GHL path |
|---|---|---|
| `victory-village-home.html` | Home / sales page | `/` |
| `victory-village-support.html` | Customer support page | `/support` |

Both pages link to each other: the home page menu and footer have a **Support** link to `https://thevictoryvillage.com/support`. If you publish the support page at a different path, search both files for `/support"` and update it.

`victory-village-home.html` is the whole page in one file: styles, content and a little script.

## Add it to GoHighLevel
1. Go to **Sites → Websites (or Funnels) →** your page → **Edit**.
2. Add a new **Section** and set it to **Full Width**. Set its padding and margin to 0 and its background to none. Do the same for its row and column.
3. Drag a **Code / Custom JS/HTML** element into the column.
4. Open the element, click **Open Code Editor**, paste the entire contents of `victory-village-home.html`, then click **Save**.
5. In **Settings → SEO / Page settings**, set the page background to `#0b0907` so no white strip shows at the edges.
6. Preview on desktop and mobile, then publish.

## Images
Your hero photo and Career Match photo are **built into the page**, so they show up as soon as you paste it. You don't need Drive links or sharing settings.
- Compressed copies are in `images/` if you ever want them in your GHL Media Library. To use a Media Library link instead, find `--hero-img` or `--match-img` at the bottom of the `<style>` block and replace everything inside `url('...')` with your link.
- **Feature cards:** AI Career Advisor, Job Board and Expert Guidance use close-up crops of your two photos (copies are in `images/card-*.jpg`). The other five cards (Resume Revamp, Live Events, Community Access, Resource Library, Ongoing Support) use built-in gold illustrations. To use your own photo on any card, follow the `IMAGE:` note above the cards in the file.
- Search the file for `IMAGE:` to see where you can add testimonial videos and headshots.

## Glowing buttons
The gold buttons glow gently and a light sweeps across them every few seconds. To tone the glow down, lower the numbers inside `@keyframes vv-glow`. To remove the light sweep, delete the `#vv .btn::after` rule. Visitors whose device is set to reduce motion see a still glow with no animation.

## Links
Search the file for `LINK:`.
- **Community Access ($47/month):** the menu's **Join the Community** button, the hero button, the plan's **Join Now** button and the bottom **Join Now** button all go to the Stripe link `https://buy.stripe.com/8x28wO80u6Hl6s2f9AdMI01`.
- **Community Plus**, **VIP Coaching** and **Try the Career Assessment** still go to `https://checkout.thevictoryvillage.com` until their links are added.
- **Log In** goes to `https://portal.thevictoryvillage.com`.

## Support page
Set it up the same way as the home page (full-width section, Custom JS/HTML element, page background `#0b0907`).

**Links to set** (search `victory-village-support.html` for `LINK:`). These are placeholders until you send the real ones:
- **Open a Ticket:** `https://thevictoryvillage.com/support-ticket`. Point it at a GHL form or survey page.
- **Schedule:** `https://thevictoryvillage.com/book-support-call`. Point it at your GHL booking calendar.
- **Email Us / General Inquiries:** `support@thevictoryvillage.com`. Replace it with your real support email.
- **Start Chat / Chat with Us:** opens the GHL chat widget if it's installed on the page (Sites → Chat Widget). If it isn't, the buttons fall back to the support email.

**What works on its own:**
- The search bar filters the FAQ as you type. Press Enter to jump to the answers.
- Clicking a help topic card (Get Started, Account & Billing, and so on) shows only the questions about that topic.
- The Live Chat card says **Online** Monday to Friday, 9 AM to 6 PM Eastern, and **Offline** the rest of the time.
- FAQ questions open and close when clicked. Edit the answers in the `<details>` blocks.

**Images:** every photo slot is listed at the bottom of the `<style>` block (search `IMAGE:`): the hero background, the "Still Need Help?" background, and the four Help Center cards. Until you send photos, each slot shows a matching gold/black placeholder.
