# � How to Fix the Vercel Build Error

Your build is failing with the error:  
`Error: > Couldn't find any 'pages' or 'app' directory.`

### 🔍 Why?
Vercel is looking at the **root** (top level) of your GitHub repository. Your actual project files are hidden inside the `portfolio-official` folder.

---

## ✅ The Fix (30-Second Dashboard Change)

You do **not** need to change any code. Follow these steps in the Vercel Dashboard:

1. Go to your **[Vercel Dashboard](https://vercel.com/dashboard)** and select your project.
2. Click the **Settings** tab at the top.
3. Click **General** on the left menu.
4. Scroll down to the **Root Directory** section.
5. Click **Edit**.
6. Select the **`portfolio-official`** folder (or type `portfolio-official` in the box).
7. Click **Save**.
8. Go back to the **Deployments** tab and click **Redeploy** on your latest build.

---

## 🏗️ Alternative: Flatten Your GitHub Repository
If you want it to work "out of the box" without settings, your GitHub repository structure should look like this:

**Current (Broken):**
```text
/ (GitHub Root)
└── portfolio-official/  <-- Vercel doesn't look inside here by default
    ├── app/
    ├── package.json
    └── ...
```

**Corrected:**
```text
/ (GitHub Root)
├── app/
├── package.json
└── ...
```

> [!NOTE]
> Setting the **Root Directory** in Vercel is the professional and easiest way to fix this!
