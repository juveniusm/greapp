# Gradient Echo — PowerPoint Content Add-in

Embeds the live Gradient Echo visualization (hosted on GitHub Pages) inside a PowerPoint slide.

## Host on GitHub Pages

1. Create a public repo named `greapp` under your GitHub account (e.g. `juveniusm/greapp`).
2. Copy `index.html` to the repo root and the `addin/` folder (with icons) alongside it. The published tree should look like:
   ```
   /index.html
   /addin/icon-64.png
   /addin/icon-128.png
   /addin/manifest.xml
   ```
3. In the repo's **Settings -> Pages**, set source to `main` branch, `/` (root).
4. After Pages builds, verify these URLs return 200:
   - `https://YOUR-USER.github.io/greapp/index.html`
   - `https://YOUR-USER.github.io/greapp/addin/icon-64.png`
   - `https://YOUR-USER.github.io/greapp/addin/icon-128.png`

If your GitHub username is not `juveniusm`, update `manifest.xml`: change every URL and the `<AppDomain>` to match your account.

## Sideload the add-in (Windows)

1. Pick a folder to act as a trusted catalog, e.g. `C:\OfficeAddins`. Right-click it -> **Properties** -> **Sharing** -> **Share** -> share with your user -> copy the network path (looks like `\\YOUR-PC\OfficeAddins`).
2. In PowerPoint: **File -> Options -> Trust Center -> Trust Center Settings -> Trusted Add-in Catalogs**.
   - Paste the network path, click **Add catalog**, tick **Show in Menu**, click **OK**, then restart PowerPoint.
3. Copy `addin\manifest.xml` from this repo into that shared folder.
4. In PowerPoint: **Insert -> Get Add-ins -> SHARED FOLDER** tab -> select **Gradient Echo** -> **Add**.

## Sideload (Mac)

Drop `manifest.xml` into:

```
~/Library/Containers/com.microsoft.Powerpoint/Data/Documents/wef/
```

(create the `wef` folder if it doesn't exist), then restart PowerPoint and use **Insert -> My Add-ins -> Developer Add-ins**.

## Notes

- The manifest GUID is `52b52d0d-e5a8-4bf0-9093-37f0e1da66a6` (distinct from the Spin Echo / T1 / T2 / Larmor add-ins so they can coexist in the same catalog). Change it again if you fork.
- `SourceLocation` and `IconUrl` must be HTTPS. GitHub Pages serves both.
- Icons live at `icon-64.png` and `icon-128.png` (currently placeholders copied from the Spin Echo add-in — swap them if you want a distinct Gradient Echo icon).
