# CodeSphere — Implementation Plan

## Product scope and implementation decisions

Build on the supplied React 19 + TypeScript + Vite site in `codesph.zip`; first restore its verified source and retain its useful page compositions, actual CodeIO logo, warm palette, typography, theme context, accessible header and shared components. The current initialized project is a static Webdev app with managed Server and Database both off. Keep it static: membership applications and event registrations are browser-local demonstrations, not secure accounts, cross-device records, outbound email or production-grade registrations. Make that boundary explicit in the interface and source comments. Production registration integrity would require a server-side store and validation; do not represent client-only checks as secure enforcement. The demo catalogue contains eight fictional records spanning all four requested explorer categories and both upcoming and past views.

Implement the site routes `/`, `/events`, `/events/:eventSlug`, `/events/:eventSlug/register`, `/registration/success/:registrationId`, `/my-registrations` and `/join`, including real event-to-detail-to-registration-to-confirmation-to-management navigation. Use Wouter with specific routes ordered before dynamic or fallback routes. Add a central event catalogue and a browser-storage registration module that owns event availability, normalized-email duplication, capacity, deadline, team-size, cancellation, unique references, and local-storage error handling. All route pages use this shared data and these rules rather than duplicating event dates. The baseline fixed date is 23 October 2026; upcoming and past records are explicitly marked fictional. Detail pages display verbatim: “Interactive demo events — fictional event details for website testing. These are not official CodeIO announcements.” Never pass off these records as official events.

Individual registration collects the required participant, academic and experience fields and agreement; NIGHTSHIFT also supports an existing team of configured size 2–4, with team name, leader, size, member names and appropriate emails, or a solo applicant who explicitly indicates that they need a team. State that solo attendees are not automatically matched. My Registrations reads only this browser's local demo data and permits cancellation only while the event configuration permits it. Membership is a separate `/join` submission with the supplied name, college email, branch, academic year, interests, experience and optional motivation fields. No form submission is transmitted; never claim email was sent or an application was received by CodeIO.

## Design system

**Design movement:** experimental digital editorial design with an underground technical-culture edge.

**Core principles:** Composition carries the identity; geometry is precise and purposeful; information stays candid and scannable; motion reinforces transitions instead of competing with content.

**Color philosophy:** Keep the supplied deep warm-black, warm brown, champagne, slate blue, lavender-grey and warm-ivory tokens. Use warm surfaces for depth, slate/lavender for readable technical clarity and champagne for precise emphasis. The supplied exact dark palette is preserved; use accessible warm-ivory and dark-ink light-theme tokens already defined in the archive rather than substituting a generic neon palette.

**Layout paradigm:** Compose a sequence of different editorial fields: asymmetric hero; typographic introduction; interactive numbered activity index; paired project folios; editorial event programme; split join/application form; and a distinct final community invitation. Event browse pages prioritize comparative date/title/category rows over repeated generic card grids.

**Signature elements:** The unchanged supplied logo in its original proportions; angular/interlocking CodeIO-inspired vector paths as original SVG artwork; and fine rules, oversized numerals and purposeful coordinates that carry a relation between sections.

**Interaction philosophy:** Make every control useful by click, touch and keyboard. Activity selection reveals actual category context. Event filters change results and counts. Registration validation preserves values and states errors beside fields. Avoid pointer-dependent functionality and automatic participant matching.

**Animation:** Use the already included `framer-motion`/Motion for React for short interface transitions where valuable and `tailwindcss-motion`, Rombo’s Tailwind plugin already in this project's dependency graph, for CSS-based opening reveals. Verify the official Tailwind v4 `@plugin` setup in the existing archive and preserve the plugin. Logo artwork itself does not change shape. A 1–2 second opening reveals its geometric composition once per browser profile, never covers or blocks navigation, and is skipped with `prefers-reduced-motion`. Keep reveal/hover transitions restrained; no scroll hijacking, fabricated loading or perpetual particle effects.

**Typography system:** Preserve Roboto 700 display/section headings and Noto Sans 400 body/forms, plus monospace only for genuine dates and system metadata. Retain the source's fluid oversized hero, readable line lengths and intentional mobile recomposition.

**Brand essence:** The BMSCE CSE community for turning technical curiosity into shared practice and institutional projects; precise, curious, independent.

**Brand voice:** Direct, energetic and unpretentious. Example lines: “BUILD BEYOND THE OBVIOUS.” and “Bring your curiosity. Find your people. Build something worth sharing.”

**Wordmark and logo:** Use the actual supplied CodeIO asset without redrawing, stretching or recolouring it; let a bespoke linked-line SVG vocabulary, not another icon, translate its geometry into the experience.

**Signature brand color:** Champagne gold `#c59d6d`, used selectively on warm dark surfaces.

## Project structure and delivery

- `client/src/App.tsx` and `client/public/manus-routes.json`: shared shell, accessible theme, page titles and all static/dynamic page patterns.
- `client/src/data/events.ts`: the complete centralized demo-event configuration, including all dates, timezone, capacities, format, deadlines, eligibility, team rules and demo flags.
- `client/src/lib/registrations.ts`: local persistence, schema guards, email normalization, unique references, rule calculations and useful recovery errors; no authentication claims.
- `client/src/components/`: existing logo, brand geometry, header, footer, controls and reusable event artwork/status/form pieces.
- `client/src/pages/`: the preserved home/events/join pages expanded for this product and pages for detail, registration, success and My Registrations.
- `client/src/index.css`: preserved palette/theme and editorial visual system with accessible, responsive states and reduced-motion rules.
- `plan.md`, `TODO.md`, `app.config.ts` and existing `client/public/assets/codeio-logo.png`: project scope/outcomes and actual supplied branding.

Use the initialized Vite static dev server on its configured port; keep its Server/Database resources disabled. Synchronize the route manifest before startup, use existing TypeScript diagnostics, run project checks/build, and inspect the functioning preview on desktop and mobile. A working preview/checkpoint is not a claim of publication. No real email integration, user authentication or server-side persistence is part of this build.

## Verified animation reference

Rombo describes a creative visual-animation toolkit and a Tailwind CSS plugin. Its official installation page documents the existing `tailwindcss-motion` package, Tailwind v4 plugin setup and CSS utility/preset classes. The archived project already has that dependency and plugin declaration, so use that verified CSS integration (not a fictitious Rombo React API). The official homepage also lists export options including Tailwind, CSS and Framer Motion. Sources: https://rombo.co/ and https://docs.rombo.co/tailwind/installation.
