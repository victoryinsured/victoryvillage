# Victory Village home page for GoHighLevel

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
Search the file for `LINK:`. Every "Join" and pricing button currently goes to `https://checkout.thevictoryvillage.com`, and **Log In** goes to `https://portal.thevictoryvillage.com`. Replace each one with the checkout URL for its plan.
