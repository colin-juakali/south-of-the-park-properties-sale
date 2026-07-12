# Marketing / visibility notes

Working list of ideas for driving buyers to the site and converting interest,
mainly aimed at supporting QR-code signage posted at the properties.

## Site changes (small, low-risk)

- [ ] Add WhatsApp links (`wa.me/254795916278`) alongside email/phone on every
      page — likely higher response rate than email for casual Kenyan buyers.
- [ ] Add Open Graph tags (`og:title`, `og:description`, `og:image`) per page
      so links shared in WhatsApp/Facebook render a proper preview instead of
      a bare URL.
- [ ] Point each plot's physical QR code straight at its detail page
      (`farm.html` / `riverside.html` / `roadside.html`), not the homepage —
      saves a tap for someone standing on-site.
- [ ] Printed fallback on signage: phone number + plot letter in plain text,
      in case the QR code fails to scan or there's no signal.
- [ ] Lightweight visit tracking — e.g. distinct query params per sign
      (`farm.html?src=sign-a`) or a privacy-friendly counter — since there's
      currently no way to tell whether the QR codes are getting scanned.

## Bigger gap

- [ ] **Real photos.** The `.photo-note` placeholders and off-site Flickr
      links are the weakest point right now. A buyer scanning a QR code on
      their phone wants to see the plot immediately, not follow an external
      link. `style.css` already has an `img.field-photo` class ready for
      this — just needs images.

## Off-site strategy (not code)

- [ ] Cross-list on BuyRentKenya, Jiji, OLX Kenya, Property24 with a link
      back to this site for full detail — most buyers search those first.
- [ ] Set up a Google Business Profile pinned at the location for local
      Maps search visibility.
