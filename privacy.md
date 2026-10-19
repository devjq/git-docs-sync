# Privacy notice: Git Docs Sync for Confluence

**Provider:** AVIRA LLC ("we").

**Contact:** avirallcdev@gmail.com.

**Effective date:** October 19, 2026.

## What the app does with data

Git Docs Sync for Confluence copies Markdown documents from a public GitHub repository that your
site admin chooses into your Confluence Cloud site as Confluence pages.

## Data the app accesses in your Confluence site

- **Spaces:** basic information about the space your admin selects (its key, id and home page),
  so the app knows where to create pages.
- **Pages:** the app creates and updates pages in that space. To avoid title clashes, it reads
  the titles of existing pages there. It changes only pages it created.
- **Permissions:** when an admin saves the settings or clicks **Sync now**, the app checks, with
  that admin's Atlassian account id, that they are a Confluence admin and can edit the target
  space. The id is used only for this check. It is not stored or logged.

## Data the app stores

The app stores the following in Forge storage, which Atlassian hosts for the app:
- the configuration your admin enters (repository, branch, folder, space, parent page,
  schedule, diagram setting);
- its record of the pages it created (source file path, page id, title and a fingerprint of the
  last content it wrote);
- the result of the most recent sync (counts, file paths and problem messages);
- a short-lived lock that stops two syncs running at once;
- a cache recording that a diagram address rendered, keyed by a fingerprint (hash) of the address,
  not the address or diagram itself.

None of these hold your document content.

We do not run our own servers for this app, and we do not copy your Confluence data elsewhere.

## Logs

The app writes operational logs to Atlassian's Forge logging. They hold only sync run ids,
counts, file paths and HTTP status codes, never page content or data about your users.

## Data sent outside Atlassian

- **GitHub.** The app downloads the selected public repository from `github.com` and
  `codeload.github.com`. Images in your documents are shown from `raw.githubusercontent.com`;
  readers' browsers load them from GitHub.
- **Diagram rendering (optional, on by default).** For Mermaid and PlantUML blocks, the diagram
  source is encoded into an image address on `mermaid.ink` (Mermaid) or `kroki.io` (PlantUML).
  The app requests each address once at sync time to check it renders, and readers' browsers
  load the image from that service. These are independent public services with their own terms.
  When your admin turns diagram rendering off, no diagram source is sent.

## Personal data and credentials

Apart from the permission check above, the app does not collect or process personal data about
your users, and it stores none. It does not use analytics or tracking, and it does not sell or
share data. It asks for no passwords, tokens or other credentials: it reads only public GitHub
repositories.

## Retention and deletion

Pages the app created stay in your Confluence site until you delete them, like any other page.
The app's stored configuration and records stay in Forge storage while the app is installed.
To request deletion of any data we hold, contact avirallcdev@gmail.com.

## Changes

We will update this notice if the app's data handling changes, and the effective date will
change with it.
