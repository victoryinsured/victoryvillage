# Victory Society pages for GoHighLevel

| File | Page | Suggested GHL path |
|---|---|---|
| `victory-village-home.html` | Home / career assessment page | `/` |
| `victory-village-membership.html` | Membership page (plans, compare, strategy sessions) | `/membership` |
| `victory-village-support.html` | Customer support page | `/support` |

The pages link to each other through `https://thevictoryvillage.com/membership` and `https://thevictoryvillage.com/support`. If you publish a page at a different path, search all three files for `/membership"` or `/support"` and update it.

`victory-village-home.html` is the whole page in one file: styles, content and a little script.

## Light membership page
The **membership page** is light from top to bottom: ivory and white backgrounds, dark text and gold accents, with only the footer dark. In the hero, the menu sits on its own ivory strip and the lounge photo fades into ivory on the left, where the headline is. The light colors live in the `LIGHT SECTIONS` style block near the top of that file; any section with `class="light"` uses them.

The **career assessment** and **support** pages stay in the original dark style.

## Add it to GoHighLevel
1. Go to **Sites → Websites (or Funnels) →** your page → **Edit**.
2. Add a new **Section** and set it to **Full Width**. Set its padding and margin to 0 and its background to none. Do the same for its row and column.
3. Drag a **Code / Custom JS/HTML** element into the column.
4. Open the element, click **Open Code Editor**, paste the entire contents of `victory-village-home.html`, then click **Save**.
5. In **Settings → SEO / Page settings**, set the page background to `#0b0907` so no white strip shows at the edges.
6. Preview on desktop and mobile, then publish.

## Hero career map
The hero shows a **Career Map** that sits right on the dark hero, inside a dark glass panel with a fine gold border, in four columns joined by curved lines:
**Where you're coming from** (burgundy; the selected one turns gold) → **Skills you already have** (gold outline) → **Claims roles you fit** (solid cream) → **Where it can lead** (quiet outline).
- Clicking a background in the left column rebuilds the map. Until someone clicks, it cycles through all five backgrounds.
- Gold lines: skills the background gives you. Thin cream lines: which skills each role uses. Dashed gold lines: where each role can lead.
- Hovering (or tapping) any pill lights up its whole route and fades everything else. Small gold dots travel along the solid lines.
- Below 1200px wide the card sits under the headline; on phones the columns become rows.
- No outside library is needed; it's plain HTML, CSS and SVG.

To change a background or its roles, edit `WEBS` in the last `<script>` of `victory-village-home.html` (`skills`, `roles`, `grow`). To add a background, add an entry to `WEBS` and its key to `ORDER`; its button appears automatically.

## Images
Your Career Match photo is **built into the page**, so it shows up as soon as you paste it. You don't need Drive links or sharing settings.
- Compressed copies of your photos are in `images/` if you ever want them in your GHL Media Library. To use a Media Library link instead, find `--match-img` at the bottom of the `<style>` block and replace everything inside `url('...')` with your link.
- **Feature cards:** AI Victory Coach, Job Board and Expert Guidance use close-up crops of your two photos (copies are in `images/card-*.jpg`). The other five cards (Resume Revamp, Live Events, Community Access, Resource Library, Ongoing Support) use built-in gold illustrations. To use your own photo on any card, follow the `IMAGE:` note above the cards in the file.
- Search the file for `IMAGE:` to see where you can add testimonial videos and headshots.

## Glowing buttons
The gold buttons glow gently and a light sweeps across them every few seconds. To tone the glow down, lower the numbers inside `@keyframes vv-glow`. To remove the light sweep, delete the `#vv .btn::after` rule. Visitors whose device is set to reduce motion see a still glow with no animation.

## Offers and links
The plans, the Toolkit-vs-Pro comparison and the four Strategy Sessions live on the **membership page**. The home page has a short **Membership** band that sends people there, and its menu has a **Membership** link and a **Join the Society** button.

| Offer | Price | Button link |
|---|---|---|
| Victory Toolkit (job-hunting tools only) | $47/month | `https://buy.stripe.com/8x28wO80u6Hl6s2f9AdMI01` (membership page, plus the home page hero and closing buttons) |
| Victory Society Pro (Toolkit + community, workshops, co-working, deeper analysis) | $97/month | placeholder `https://checkout.thevictoryvillage.com` |
| 1:1 Strategy Session | $100 one-time add-on, 10 per quarter | placeholder `https://checkout.thevictoryvillage.com` (pricing card and the four "Book this session" links) |
| Career assessment | | placeholder: "Try the Career Assessment" on the home page still goes to `https://checkout.thevictoryvillage.com` until you send the assessment link |

Search each file for `LINK:` to find every button. **Log In** goes to `https://portal.thevictoryvillage.com`.

## Membership page
Set it up like the others (full-width section, Custom JS/HTML element, page background `#0b0907`). It has: a hero with your Victory Society Membership lounge photo (on desktop it fills the right of the hero at its true shape and fades softly into black on the left, where the headline sits; on phones the whole photo shows under the menu with the headline below; to swap it, replace the `src` of the image marked `IMAGE:` in the hero), How It Works in three steps, the three plans, a Toolkit-vs-Pro comparison table, the four Strategy Sessions, membership FAQs, and a closing call to action. The FAQ about upgrading says members contact support to switch plans; change it if upgrading works another way.

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
