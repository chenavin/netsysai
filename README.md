# NetSysAI 2026 website

A static one-page site for the NetSysAI workshop (19 Nov 2026, BGU). There is no build step: edit `index.html`, commit, and GitHub Pages republishes the site within about a minute.

```
index.html          all content (sections are marked with HTML comments)
style.css           look & feel (colors are defined at the top)
netsysai-2026.ics   "Add to calendar" file
assets/             logo mark, speaker photos, partner logos, link-preview image
.nojekyll           tells GitHub Pages to serve files as-is
```

## 1. Publish on GitHub Pages (one time)

1. On GitHub, create a new **public** repository named `netsysai` under the `chenavin` account.
2. Upload all the files in this folder, including `.nojekyll` and `assets/`, and commit. You can use **Add file → Upload files**; drag in the folder contents.
3. Go to **Settings → Pages → Build and deployment**. Set Source to **Deploy from a branch**, Branch to **main**, folder to **/ (root)**, then **Save**.
4. After about a minute the site is live at **https://chenavin.github.io/netsysai/**.

Optional: link to it from your homepage repo (`chenavin.github.io`).

## 2. Create the registration form (Google Forms)

Suggested title: **NetSysAI 2026: Registration**

| # | Question | Type | Required |
|---|----------|------|----------|
| 1 | Full name | Short answer | ✔ |
| 2 | Email | Short answer (response validation: email) | ✔ |
| 3 | Affiliation (university / company) | Short answer | ✔ |
| 4 | Position | Multiple choice: Faculty · Postdoc · PhD student · MSc student · BSc student · Industry · Other | ✔ |
| 5 | Will you attend in person? | Multiple choice: Yes · Maybe | ✔ |
| 6 | Dietary requirements | Checkboxes: None · Vegetarian · Vegan · Gluten-free · Other | |
| 7 | Will you arrive by car? (for campus parking permits) | Multiple choice: Yes · No | |
| 8 | I agree that my name and affiliation may appear in the participants list | Checkbox | |

Settings: turn on **Collect email addresses** and link the form to a Google Sheet (Responses → Link to Sheets).
Short-talk applications for the graduate student session are not part of the form: students email the organizers directly (title, abstract, relevant publications).

Then **Send → link icon → Shorten URL**, copy the `https://forms.gle/...` link, and in `index.html` set:

```html
const REGISTRATION_URL = "https://forms.gle/XXXXXXXX";
```

Every Register button on the page will then open the form. While the value is empty, the buttons say "Registration opens soon".

> Note: the poster shows `forms.gle/netsysai-2026`. Google generates random short links, so that exact address won't exist. Update the poster with the real link, or point it to the website instead.

## 3. Common updates

- **Talk title**: edit the `<p class="talk">` line in the speaker's card, and the matching row in the Program table.
- **Speaker photo**: add a square JPG (about 400×400) to `assets/speakers/`. Then replace `<div class="avatar" …>AA</div>` with `<img class="avatar" src="assets/speakers/aharoni.jpg" alt="Asaf Aharoni">`.
- **Program row**: copy a `<tr>` in the Program table. Add `class="key"` to highlight a talk, or `class="break"` for a coffee or lunch break. Remove the "Tentative" tag once the program is final.
- **Company logos**: save the official logo file (SVG preferred) as `assets/logos/nvidia.svg` and so on. In the "Speakers from" strip, replace `<span class="wordmark">NVIDIA</span>` with `<img src="assets/logos/nvidia.svg" alt="NVIDIA">`. Logos are shown in grayscale and turn to color on hover.
- **Venue**: fill in the building and hall ("Building and hall: TBA") and the parking details.
- **Dates**: set the "TBA" deadlines in the Participate section.
- Update "Last updated" in the footer.
