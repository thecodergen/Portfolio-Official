# Fixing Vercel Deployment: "Missing `app` Directory"

Vercel fails to build your project because it expects to find the `package.json` and `app` folder at the **root** of your repository. Based on your folder structure:

```text
Portfolio/ (Root of GitHub Repo)
   portfolio-official/ (Subdirectory)
      app/
      package.json
```

Vercel is looking inside `Portfolio/` and seeing nothing to build.

## Option 1: Fix via Vercel Settings (Recommended)

You don't need to change your code or move files. You just need to tell Vercel where your project starts.

1. Go to your **Vercel Dashboard**.
2. Select your project.
3. Go to **Settings** > **General**.
4. Find the **Root Directory** field.
5. Click **Edit** and select the `portfolio-official` folder (or type `portfolio-official`).
6. Click **Save**.
7. Go to the **Deployments** tab and click **Redeploy**.

## Option 2: Restructure your Repository

If you want the project to build automatically without special settings, move the contents of `portfolio-official` directly into the `Portfolio` root.

### Steps to move files using Terminal:
If you are at the root of your repository in the terminal:

```bash
# Move all files up one level (Linux/Mac/WSL)
mv portfolio-official/* ./
mv portfolio-official/.* ./  # to move hidden files like .eslintrc
rmdir portfolio-official
```

### For Windows PowerShell:
```powershell
Move-Item -Path .\portfolio-official\* -Destination .\
Remove-Item -Path .\portfolio-official
```

## Summary of Correct Structure for Vercel
Your repository's root directory should look like this:
```text
/ (Repo Root)
├── app/
├── components/
├── public/
├── package.json
└── next.config.js
```

---
> [!TIP]
> **Option 1** is the fastest fix if you prefer keeping your nested folder structure!
