# Liu Lab Independent Website Prototype

Static HTML prototype for a modern, recruiter-friendly academic lab website. It avoids Yale logos, seals, official Yale colors as branding, and any language implying this is an official Yale website. Yale affiliation should be stated only as factual appointment text once confirmed.

## Design Rationale

The revised direction is restrained, cinematic and paper-specific. The site now centers the SLC33A1 story from the attached Nature Cell Biology paper rather than generic biomedical language:

- ER immunopurification and compartment-specific profiling.
- ER redox metabolomics, especially GSH/GSSG balance.
- ER-GshF stress model and ER-focused CRISPR screening.
- SLC33A1 as an ER-localized oxidized glutathione transporter.
- Cryo-EM and molecular dynamics insight into GSSG recognition.
- PDI oxidation, UPR/ER stress, ERAD dependency and disease relevance.

Typography and spacing were reduced from the first pass so the site feels more like a polished independent academic lab site and less like an oversized startup landing page.

The hero uses the supplied silent molecular/ER video with a solid black left-side reading field and a gradual fade to the scientific visual. The former WebGL molecule/process animation has been replaced with a compact evidence map so the SLC33A1 mechanism reads more like a research narrative than a graphics demo.

## Current Structure

- `index.html`: semantic one-page prototype with anchored sections.
- `styles.css`: responsive visual system, layout, typography and component styling.
- `content/site-content.js`: update-friendly content records for research, process stages, publications, people, roles, news and contact.
- `scripts/app.js`: content rendering, mobile navigation, autoplay video handling and icon initialization.
- `assets/`: optimized web images used by the prototype.
- `references/`: local source/archive files, including the attached paper PDF and original lab-provided TIF.

## Ownership and Hosting

The repository is owned by Shanshan's GitHub account:

- Repository: https://github.com/shanshanliu1218-oss/ShanShanLiuLab
- Public site: https://shanshanliulab.com/
- GitHub Pages source: `main` branch, project root (`/`)
- GitHub Pages custom domain: `shanshanliulab.com`
- HTTPS: enforced in GitHub Pages settings

The root `CNAME` file must stay as:

```txt
shanshanliulab.com
```

Do not change the repo `CNAME` file to `www.shanshanliulab.com`. The canonical site is the apex domain, and `www` should redirect to it.

Expected DNS records at the domain registrar:

```txt
A      @      185.199.108.153
A      @      185.199.109.153
A      @      185.199.110.153
A      @      185.199.111.153
CNAME  www    shanshanliu1218-oss.github.io
```

If the repository is transferred again, update the `www` CNAME target to the new GitHub Pages owner host, usually `<new-owner>.github.io`. The apex `A` records should remain the GitHub Pages IPs above.

Local git remotes for active maintenance should point to:

```bash
git remote set-url origin https://github.com/shanshanliu1218-oss/ShanShanLiuLab.git
```

## Source Notes

Primary source:

- Local PDF: `references/s41556-026-01922-y.pdf`
- Nature article: https://www.nature.com/articles/s41556-026-01922-y

Content currently emphasized from the PDF and article:

- ER immunopurification using an EMC3-based ER tag.
- ER metabolome profiling of redox metabolites, UDP-sugars, nucleotides and lipid-associated metabolites.
- ER-GshF stress modeling and ER-focused CRISPR screening.
- SLC33A1 as an ER-localized GSSG exporter supported by uptake and liposome counterflow assays.
- Cryo-EM and molecular-dynamics interpretation of GSSG recognition in the SLC33A1 central cavity.
- PDI oxidation, UPR/ER stress and ERAD dependency as cellular outcomes of ER redox imbalance.

Additional publication/context sources:

- Rockefeller story: https://www.rockefeller.edu/news/39407-antioxidant-glutathione-protein-regulation-cancer-neurodegeneration/
- Science publication DOI: https://doi.org/10.1126/science.adf4154
- Google Scholar profile supplied by user: https://scholar.google.com/citations?user=nDvllAYAAAAJ&hl=en
- ORCID: https://orcid.org/0000-0001-8293-1025

Google Scholar was not fully machine-readable in this environment. The publication list should be reconciled against a CV, Scholar export, ORCID export or PubMed list.

## Asset Notes

- `assets/molecular-er-reference.png`: user-provided molecular/ER visual benchmark.
- `assets/liu-lab-hero-loop.mp4`: optimized silent hero background video used on the live homepage.
- `assets/liu-lab-hero-poster.jpg`: poster image for the live hero video.
- `assets/molecular-er-hero.webp` and `.jpg`: earlier optimized still versions retained as fallback/reference assets.
- `assets/molecular-er-hero-motion.mp4`: earlier silent motion hero video retained as a source/reference asset.
- `references/22-49-3_Beads_035.tif`: original lab-provided ER pulldown beads TIF from Shanshan.
- `assets/beads-microscopy-crop.webp` and `.jpg`: cropped, web-optimized versions used as the Join section background.
- `assets/erip-beads-*.webp` and `.jpg`: cropped, web-optimized ER-IP bead microscopy slideshow images generated from lab-provided TIFs. The bottom microscope metadata strip was removed for web presentation.
- `assets/erip-transporters-process.mp4`: muted, web-optimized ER-IP process video used in the SLC33A1 mechanism section.
- `assets/publication-slc33a1-sketch.webp` and `.jpg`: web-optimized publication preview sketch for the featured 2026 SLC33A1 paper.
- `assets/publication-cell-metabolism-2021-cover.webp` and `.jpg`: web-optimized cover preview for the 2021 Cell Metabolism paper.
- `references/research-program-*.jpeg`: Shanshan-provided research-direction sketches.
- `assets/research-program-*.webp`: optimized web versions used in the Research Program section.
- `assets/er-microscopy.png`: earlier microscopy placeholder retained locally but no longer primary.

Confirm rights and preferred attribution language for user-provided images before public deployment.

## Future Next.js or Astro Migration

The static architecture maps cleanly to:

- `components/Navbar.tsx`
- `components/Hero.tsx`
- `components/ResearchCard.tsx`
- `components/PublicationCard.tsx`
- `components/PersonCard.tsx`
- `components/NewsRow.tsx`
- `components/CTASection.tsx`
- `components/Footer.tsx`
- `content/research.ts`
- `content/publications.ts`
- `content/people.ts`
- `content/news.ts`

## Local Preview

Open `index.html` directly or serve the folder:

```bash
python -m http.server 4173
```

Then visit `http://localhost:4173`.

## Deployment

This site is currently deployed with GitHub Pages, not Vercel.

Current deployment workflow:

1. Make edits locally.
2. Preview with `python -m http.server 4173`.
3. Commit changes to `main`.
4. Push to `origin main`.
5. GitHub Pages serves the static files from the repository root.
6. Verify the live site at https://shanshanliulab.com/.

There is no build command and no package install step for the current static version.

Useful live checks:

```bash
curl -I https://shanshanliulab.com/
curl -I https://www.shanshanliulab.com/
curl -I https://shanshanliulab.com/assets/liu-lab-hero-loop.mp4
```

Expected behavior:

- `https://shanshanliulab.com/` returns `200 OK`.
- `https://www.shanshanliulab.com/` redirects to `https://shanshanliulab.com/`.
- GitHub Pages reports `status=built`, `cname=shanshanliulab.com`, and HTTPS enforced.

## Maintenance Notes

- Keep public copy factual and source-grounded.
- Do not use Yale logos, seals or official Yale branding unless explicit permission is provided.
- Keep production-ready media optimized in `assets/`; large raw exports should generally stay local or in `references/` only when there is a clear archival reason.
- Update `content/site-content.js` for routine text, publication, people, news and contact changes.
- Update `sitemap.xml` only if real standalone pages are added. Anchor sections on this one-page site do not need separate sitemap entries.

For a future Astro or Next.js version, move the content records into typed modules and use the framework build command.
