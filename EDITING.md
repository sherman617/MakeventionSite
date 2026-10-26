# Editing the Makevention website

You don't need to know any code. Changes are made in **Pages CMS**, a free editor that runs in your browser and saves straight to this GitHub repository.

## One-time setup

1. Make a free GitHub account at <https://github.com/signup> if you don't have one.
2. Ask the site admin to add you as a collaborator on the `MakeventionSite` repository. Accept the email invitation.
3. Go to <https://app.pagescms.org>, choose **Sign in with GitHub**, and open **MakeventionSite**.
   - The first time, Pages CMS asks to be installed on your GitHub account. Allow it for this repository.

## How a change goes live

There are two copies of the site:

| Copy | Address | Branch |
| --- | --- | --- |
| **Preview** — only for checking your work | `…/preview/` | `staging` |
| **Live** — what the public sees | the normal address | `main` |

1. In Pages CMS, check that the branch picker at the top shows **staging**. It opens on staging by default.
2. Edit a page and click **Save**.
3. Wait about a minute, then open the preview copy, which has a yellow "Preview copy" bar at the top. Refresh the page to see your change.
4. When it looks right, click **Publish preview to live site** under **Actions** in Pages CMS and confirm. The live site updates in a minute or two.

> The preview copy is public if someone knows the address, but search engines are told to ignore it.

## What's where

- **Pages** — every page on the site. Each page is a list of *blocks* you can add, reorder or remove:
  - *Colored heading*: the big colored bars, such as "Exhibitors" in orange.
  - *Text*: regular paragraphs, lists and links.
  - *Side-by-side boxes*, *Two columns*, *Image*, *Video*, *Quote box*, *Highlighted text*, *Google map*, *PayPal donate button*, *Blank space*.
- **Menu** — the links across the top and in the footer.
- **Sponsors** — sponsor levels and logos. These show on both the Home and Sponsors pages.
- **Site settings** — header image, tagline and footer text.
- **Media** — upload images and PDFs here. To link a PDF, upload it, copy its address, and use it as a link in a Text block.

## Common jobs

- **Open the exhibitor or volunteer application**: edit *Exhibitors* or *Volunteers*. Replace the "will open in February" sentence with a link to the form, for example `[Apply to exhibit](https://…)`.
- **New year's sponsors**: edit *Sponsors* in the sidebar. Change the year in the "Special thanks to our 2025 Sponsors!" heading on the Home page and the "2025 Sponsors:" heading on the Sponsors page.
- **Add a page**: in *Pages*, click **Add an entry**, give it a title, and add blocks. Then add it to the *Menu* with the link `/your-page-title/`. The link is the title in lowercase, with dashes instead of spaces.

## If something goes wrong

Every save is kept in the history, so nothing is lost. Ask the site admin to undo a change, or look under the repository's **Actions** tab. A red ✗ there means the last build failed and shows which file caused it.
