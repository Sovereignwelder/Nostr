# Welding Inspector – Static Site

**Live URL:** https://welding-inspector.us  

A lightweight, SEO‑optimized, fully static website built for a Certified 
Welding Inspector (CWI) serving Pinellas, Pasco, and Hillsborough 
counties. The site is designed to be hosted on **Cloudflare Pages** (or 
any other static‑site host).

---

## Table of Contents
- [Features](#features)
- [Folder Structure](#folder-structure)
- [SEO & Accessibility](#seo--accessibility)
- [How to Deploy to Cloudflare Pages](#how-to-deploy-to-cloudflare-pages)
- [Adding / Updating Blog Posts](#adding--updating-blog-posts)
- [License](#license)

---

## Features
- **Local‑SEO ready** – meta tags, JSON‑LD `LocalBusiness`, canonical 
  URLs, Open Graph.
- **Responsive design** – mobile‑first CSS, grid layout, fluid images.
- **Static & fast** – no server‑side code, ideal for Cloudflare Pages edge 
  cache.
- **Dynamic‑like blog** – a tiny JavaScript object (`posts`) drives both 
  the homepage featured article and the blog archive, so adding a post 
  updates both places automatically.
- **Floating “Contact Us” button** – persistent call‑to‑action linking to 
  a Cal.com scheduler.
- **Separate media folder** (`/media`) that isn’t exposed in navigation.
- **Robots, sitemap, CNAME** ready for search engines and custom domain.
- **MIT licensed** – free to modify and reuse.

---

## Folder Structure

```
/
│
├─ index.html                # Home / landing page
├─ blog/
│   ├─ index.html            # Blog archive (JS‑generated list)
│   ├─ procedure-qualification.html
│   ├─ welder-certifications.html
│   └─ vt-inspection-trends.html
├─ contact.html              # Plain‑text contact info
├─ thankyou.html             # Hidden thank‑you page (form target)
│
├─ media/                    # Image placeholders (not linked in 
navigation)
│   ├─ hero.jpg
│   ├─ featured.jpg
│   ├─ proc-qual.jpg
│   ├─ welder-cert.jpg
│   └─ vt-inspection.jpg
│
├─ robots.txt
├─ sitemap.xml
├─ CNAME                     # Cloudflare Pages custom‑domain file
└─ README.md
```

---

## SEO & Accessibility Highlights
| Element | Implementation |
|---------|----------------|
| **Title & Meta Description** | Unique, keyword‑rich per page. |
| **Open Graph / Twitter Cards** | Populated for rich social previews. |
| **JSON‑LD LocalBusiness** | Provides address, phone, service area, and 
  qualification data to AI‑driven search. |
| **Alt Text** | Every image includes descriptive `alt` attributes. |
| **Semantic HTML** | Proper headings (`h1`‑`h3`), `article`, `section`, 
  and ARIA labels for the floating button. |
| **Responsive Images** | `loading="lazy"` and CSS that scales to any 
  viewport. |
| **Fast Load** | No external libraries, minimal inline CSS/JS. |
| **Robots & Sitemap** | Allow all, point to sitemap for crawl efficiency. |

---

## How to Deploy to Cloudflare Pages

1. **Create a Git repository** (GitHub, GitLab, Bitbucket).  
2. **Push the entire folder structure** (including `CNAME`).  
3. In Cloudflare Dashboard → **Pages → Create a Project** → connect your 
   repo.  
4. Set **Build settings**:  
   - **Framework preset**: *None* (static).  
   - **Build command**: leave blank.  
   - **Build output directory**: `/` (root).  
5. Click **Save and Deploy**.  
6. Add your custom domain in Cloudflare DNS and ensure the `CNAME` file 
   contains `welding-inspector.us`.

*Cloudflare will automatically serve the site from the edge, giving you 
sub‑second load times worldwide.*

---

## Adding / Updating Blog Posts

All blog data lives in a **single JavaScript array** named `posts`.  
When you add a new post, simply:

1. **Create the HTML file**  
   - Place it under `/blog/` (e.g., `my-new-post.html`).  
   - Follow the same head/meta structure as the other posts.  
   - Add a relevant image in `/media/` and reference it with an `alt` tag.

2. **Update the `posts` array** (found in both `index.html` and 
   `blog/index.html`).  
   ```js
   const posts = [
     // existing objects …
     {
       title: "My New Post Title",
       slug: "my-new-post",                     // not used 
  programmatically, just for reference
       excerpt: "A brief 1‑2 sentence summary of the article.",
       img: "/media/my-new-image.jpg",
       alt: "Descriptive alt text for the new image",
       url: "/blog/my-new-post.html"
     }
   ];
   ```
3. **Commit & push** – the homepage will automatically display the newest 
   post as the featured article, and the blog archive will list it among the 
   others.

*No additional HTML editing is required beyond the new post page itself.*

---

## License

```
MIT License

Copyright (c) 2026 Justin Bryan

Permission is hereby granted, free of charge, to any person obtaining a 
copy
of this software and associated documentation files (the "Software"), to 
deal
in the Software without restriction, including without limitation the 
rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

[...standard MIT text...]
```