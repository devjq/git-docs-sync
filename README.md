# Git Docs Sync for Confluence

Git Docs Sync for Confluence is a Confluence Cloud app. It publishes the Markdown files in a
folder of a public GitHub repository as native Confluence pages. The pages are ordinary
Confluence content, so Confluence search, page history and permissions all work on them.

The app is a free beta on the Atlassian Marketplace, provided by AVIRA LLC.

- [Privacy notice](privacy.md)
- [End user terms](eula.md)
- Support: avirallcdev@gmail.com, or [open an issue](https://github.com/devjq/git-docs-sync/issues)

## Set up

You need a Confluence Cloud site where you are a site admin, and a public GitHub repository.

1. Install **Git Docs Sync for Confluence** from the Atlassian Marketplace.
2. Open the app's configuration page: select **Git Docs Sync** in Confluence's settings, or
   select **Configure** next to the app where you manage apps.
3. Fill in the settings below and select **Save**.
4. Select **Sync now**. When the sync finishes, the page shows its report.

| Setting | What to enter |
|---|---|
| GitHub repository (public) | `owner/name`, or the repository's github.com address |
| Branch | Leave empty to use the repository's default branch |
| Folder | The folder that holds your docs, such as `docs`. Leave empty for the whole repository |
| Confluence space key | The key of the space that receives the pages, such as `DOCS` |
| Parent page id | Optional. Leave empty to place the pages under the space's home page |
| Render Mermaid and PlantUML diagrams | On by default. See [Diagrams](#diagrams) |
| Schedule | Off, Hourly or Daily |

Only a Confluence admin who can edit the target space can save the settings or start a sync.

Changing the repository, folder, space or parent page starts a fresh sync. Pages from the old
source stay in place and are no longer updated.

## What a sync does

- Each Markdown file becomes one Confluence page. Each subfolder that holds Markdown becomes a
  parent page, so your folder tree becomes the page tree. A folder's `README.md` becomes that
  folder's page.
- A page's title is the file's first level-1 heading. Without one, the title is the file name,
  made readable: `setup-guide.md` becomes "Setup guide". If the title is already used in the
  space, the folder path is added in parentheses, such as "Setup Guide (docs/guide)".
- Links between your docs open the matching Confluence page, including links to a heading.
  Links to other files in the repository open them on GitHub. Web and email links stay as they
  are.
- Images are shown in place. Images stored in the repository load from GitHub.
- Code blocks become Confluence code blocks. Tables and task lists carry over. HTML the app does
  not support is shown as text and never run.
- Every synced page starts with a note that links to its source file on GitHub. Edit the
  Markdown on GitHub, not the page: a page is rewritten the next time its file changes.
- A re-sync updates only pages whose file changed, and never creates a second page for the same
  file.
- Files removed from the repository are listed in the sync report. Their pages are not deleted.
- If someone deletes a synced page in Confluence, the next sync creates it again.
- The app changes only pages it created.
- Only one sync runs at a time. The sync report lists what was created, updated, unchanged or
  failed, and why.

## Diagrams

With diagram rendering on, fenced code blocks tagged `mermaid` or `plantuml` show as images. The
diagram source is sent inside the image address to mermaid.ink (Mermaid) or kroki.io
(PlantUML), which are independent public services with their own terms. Readers' browsers load
the images from there. With rendering off, the blocks stay as code and no diagram source leaves
Atlassian.

## Free beta limits

- Public GitHub repositories only.
- One repository folder per Confluence site.
- Up to 500 Markdown files per sync, taken in alphabetical path order.
- Markdown files over 1 MB are skipped and listed in the sync report.

## Security

Report a security problem to avirallcdev@gmail.com.
