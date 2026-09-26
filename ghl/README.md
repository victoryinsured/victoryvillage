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
Your two Drive photos are already linked near the top of the `<style>` block (`--hero-img` and `--match-img`).
- The Drive files must be shared as **Anyone with the link → Viewer**, or they won't show up.
- For faster loading, upload both photos to **GHL → Media Library**, copy their URLs, and paste them in place of the Drive links.
- Search the file for `IMAGE:` to see where you can add photos to the feature cards, testimonial videos and headshots.

## Links
Search the file for `LINK:`. Every "Join" and pricing button currently goes to `https://checkout.thevictoryvillage.com`, and **Log In** goes to `https://portal.thevictoryvillage.com`. Replace each one with the checkout URL for its plan.
