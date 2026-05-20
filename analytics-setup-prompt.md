# Stappenplan voor je AI-coder: privacy-vriendelijke webanalytics op een statische site

Voor een statische HTML-pagina (GitHub Pages, Netlify, Vercel, of een eigen webserver). Geeft je pageviews, scroll-diepte, CTA-klikken en traffic-bron, zonder cookies en zonder cookiebanner. Werkt op elke pagina-lengte en faalt stil als de tracker geblokkeerd wordt.

---

## Voorvereisten (door de site-eigenaar)

1. Maak een gratis Umami Cloud-account op https://cloud.umami.is
2. Voeg een nieuwe website toe; vul het domein in (dit is alleen metadata in het dashboard)
3. Kopieer de **Website ID** (UUID) — die heb je in stap 1 nodig

Te vervangen tijdens implementatie:

| Placeholder | Waarde |
|---|---|
| `YOUR_UMAMI_WEBSITE_ID` | de UUID uit Umami Cloud |
| `PAGE_IDENTIFIER` | korte slug per pagina, bijv. `blog-2026-01` of `case-acme` |
| `CTA_DESTINATION_URL` | de bestemmings-URL van je primary call-to-action |
| `CTA_EVENT_NAME` | korte event-naam, bijv. `cta-intake-click` of `cta-signup` |

---

## Stap 1 — Plaats de Umami-tracker in `<head>`

Vlak vóór `</head>`:

```html
<!-- Umami Cloud — cookieless analytics, AVG-conform. -->
<script defer src="https://cloud.umami.is/script.js" data-website-id="YOUR_UMAMI_WEBSITE_ID"></script>
<script>
  // Labelt deze pageview voor dashboard-filtering wanneer je meer pagina's hebt.
  window.addEventListener('load', function () {
    if (window.umami && typeof window.umami.identify === 'function') {
      window.umami.identify({ article: 'PAGE_IDENTIFIER' });
    }
  });
</script>
```

## Stap 2 — Tag de primary CTA met een event + UTM-parameters

Op de primary call-to-action-link:

```html
<a href="CTA_DESTINATION_URL?utm_source=blog&utm_medium=cta&utm_campaign=PAGE_IDENTIFIER"
   data-umami-event="CTA_EVENT_NAME">
  Jouw CTA-tekst hier
</a>
```

De UTM-parameters maken de klik traceerbaar in de analytics van de bestemmings-site, zodat je weet dat een klant via dit artikel binnenkwam.

## Stap 3 — Voeg de scroll-depth tracker toe vóór `</body>`

```html
<script>
  // Scroll-depth tracker: stuurt 25/50/75/100% bereikte leesdiepte naar Umami.
  // Faalt stil als Umami nog laadt of geblokkeerd is.
  (function () {
    var milestones = [25, 50, 75, 100];
    var fired = {};
    function check() {
      var scrolled = window.scrollY + window.innerHeight;
      var total = document.documentElement.scrollHeight;
      if (total <= window.innerHeight) return;
      var pct = Math.round((scrolled / total) * 100);
      for (var i = 0; i < milestones.length; i++) {
        var m = milestones[i];
        if (pct >= m && !fired[m]) {
          fired[m] = true;
          if (window.umami && typeof window.umami.track === 'function') {
            window.umami.track('scroll-' + m);
          }
        }
      }
    }
    window.addEventListener('scroll', check, { passive: true });
    window.addEventListener('load', check);
  })();
</script>
```

Geen variabelen om in te vullen — werkt out-of-the-box op elke pagina-lengte.

## Stap 4 — UTM-discipline voor traffic-bron-tracking

Gebruik UTM-parameters op elke link náár deze pagina vanuit externe kanalen:

```
?utm_source=KANAAL&utm_medium=TYPE&utm_campaign=PAGE_IDENTIFIER
```

Conventies (consistent houden tussen campagnes):

| Parameter | Waarden | Voorbeeld |
|---|---|---|
| `utm_source` | `linkedin`, `twitter`, `email`, `youtube`, `newsletter` | platform-naam |
| `utm_medium` | `social`, `email`, `referral`, `cpc` | type kanaal |
| `utm_campaign` | gelijk aan `PAGE_IDENTIFIER` | matcht de pagina-slug |

Voorbeelden:
- LinkedIn-comment: `https://jouwsite.com/blog-2026-01.html?utm_source=linkedin&utm_medium=social&utm_campaign=blog-2026-01`
- Nieuwsbrief-link: `https://jouwsite.com/blog-2026-01.html?utm_source=newsletter&utm_medium=email&utm_campaign=blog-2026-01`

---

## Verificatie

Test in een incognito-venster (anders telt je eigen sessie mee):

1. **Pageview** — open de pagina, check binnen 30 seconden of een pageview in Umami verschijnt
2. **Scroll-events** — scroll naar het einde, verifieer `scroll-25`, `scroll-50`, `scroll-75`, `scroll-100` events
3. **CTA-event** — klik de CTA-knop, verifieer `CTA_EVENT_NAME` event
4. **Bron-attributie** — open via een UTM-link, verifieer dat de bron correct is toegewezen
5. **Cookieless** — DevTools → Application → Cookies → bevestig dat er geen cookies worden gezet

---

## Scope-disclaimer

Umami trackt alleen pagina's waarin dit script daadwerkelijk staat. Andere pagina's onder hetzelfde domein zijn onzichtbaar in jouw dashboard zolang je het script daar niet plakt. Plak het dus bewust per pagina die je wilt meten.

## Wanneer je dit pad ontgroeit

- **Meer dan 10.000 events per maand**: upgrade van Umami Cloud free naar paid (~$9/mnd) of switch naar Plausible / Simple Analytics.
- **Funnel-analyse, A/B-testen, heatmaps**: switch naar Matomo of een vergelijkbaar zwaarder tool.
- **Per-product gescheiden dashboards**: maak meerdere Umami-websites met aparte UUIDs in plaats van één gedeelde site.
