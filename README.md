# Nacita Material Control Tower

Material planning and stock supervision for Nacita Logistics: MRO, packing, hospitality and cleaning items across the four business units (Warehousing 3PL, Last Mile, Fleet & Technical, IOR).

## The three versions

| File | Who | What they can do |
|---|---|---|
| `index.html` | **Viewers** – share this link | See everything (dashboard, item master, stock, Min/Max, movements, POs, audit log) and export to Excel/CSV. Nothing can be changed. |
| `editor.html` | **Editors** (storekeepers, planners) | Everything viewers can, plus: edit item details, set SS / Min / Max, post stock movements, approve the parameter review, and create, approve and receive POs. Publish changes. |
| `admin.html` | **Admin** | Everything editors can, plus: create, copy and delete items, Excel mass upload, planning policy settings, restore backups and reset the data. Publish changes. |

Site address after setup: `https://YOUR-USERNAME.github.io/nacita-material-control/`
(viewer = that address, editor = `…/editor.html`, admin = `…/admin.html`)

## How the data works

* All three pages read the same file: `data/nacita-data.json`.
* Admins and editors work on a copy that is kept in their own browser. Nobody else sees the changes until they click **Publish**.
* **Publish** writes the file to this repository through the GitHub API. GitHub Pages updates the site, and viewers see the new version within about 1–2 minutes. Viewers also refresh automatically every 5 minutes, or straight away with the ⟳ button.
* Each publish is a commit, so the repository's commit history is a full version history of the data. Any earlier version can be restored from GitHub.
* If two people edit at the same time, the second person to publish is warned and can choose to load the newer version first.

## Access tokens (who is allowed to publish)

Publishing needs a GitHub **fine-grained personal access token** with access to this repository only:

1. GitHub → your picture (top right) → **Settings** → **Developer settings** → **Personal access tokens** → **Fine-grained tokens** → **Generate new token**.
2. Name: e.g. `nacita-editor-Ahmed`. Expiration: 90 days, for example.
3. **Repository access** → *Only select repositories* → `nacita-material-control`.
4. **Permissions** → **Repository permissions** → **Contents** → **Read and write**.
5. **Generate token** and copy it right away (GitHub shows it only once).
6. In `admin.html` or `editor.html` → **Settings & Data** → **GitHub connection…** → paste the token, enter the person's name → **Test connection** → **Save**.

Create one token per person, so a single token can be revoked (GitHub → Fine-grained tokens → Delete) without affecting anyone else. Send tokens privately, never by e-mail to a group.

## Important limits

* A free GitHub account can only publish a site from a **public** repository, so the pages **and the data file can be opened by anyone who has or guesses the link**. Don't store confidential prices or personal data unless that is acceptable. For a login-protected site, see the options in the setup notes.
* The admin/editor split is a matter of which page a person uses. What actually controls who can change the published data is the **token**: without a token, nobody can publish.
* Photos are stored inside the data file. Keep them to what's useful; the file should stay under ~50 MB.
