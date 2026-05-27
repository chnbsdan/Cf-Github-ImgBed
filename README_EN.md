<div align="center">
<h1>Cf-Github-ImgBed</h1>
<p>A lightweight image hosting service based on Cloudflare Pages + GitHub API. No server required, zero-cost deployment.</p>

<img src="https://img.shields.io/badge/version-v2.0-blue" />
<a href="https://github.com/Stoeaves/Cf-Github-ImgBed/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" /></a>
<a src="https://pages.cloudflare.com"><img src="https://img.shields.io/badge/platform-Cloudflare%20Pages-orange" /></a>

<br/>
<a href="https://docs.stoeaves.com/cf-github-imgbed/">Documentation</a> · 
<a href="https://github.com/Stoeaves/cf-github-imgbed/issues">Feedback</a> ·
<a href="https://docs.stoeaves.com/cf-github-imgbed/update-log.html">Changelog</a>

<br/>

<a href="https://github.com/Stoeaves/Cf-Github-ImgBed/blob/main/README.md">简体中文</a> | English

<br />

<a src="https://github.com/Stoeaves/cmb/fork"><img src="https://img.shields.io/badge/GitHub-Fork%20this%20Repository-181717?style=for-the-badge&logo=github" /></a><br/>
<a src="https://dash.cloudflare.com/?to=/:account/workers-and-pages/create/pages"><img src="https://img.shields.io/badge/Go%20to-Cloudflare%20Pages-F38020?style=for-the-badge&logo=cloudflare&logoColor=white" /></a>

</div>

## ✨ Features

- 🚀 **Cloudflare Pages Deployment** — Global CDN acceleration, zero cost
- 🔐 **AES + RSA Encryption** — Secure admin login
- 📱 **TOTP 2FA** — Supports Google Authenticator
- 📤 **Batch Upload** — Drag & drop, paste, batch management
- 🗂️ **Multi-Repository Support** — Independent token & CDN per repo
- 🎨 **Customizable Themes** — 8 presets + custom colors
- 🌐 **Internationalization** — English / 简体中文
- 🔍 **Local Search & Sorting** — By name, date, size
- 🖼️ **Image Editing** — Format conversion, quality compression, resizing
- 📋 **Batch Actions** — Select, delete, public/private, export
- 📥 **Export Links** — URL / Markdown / HTML / JSON / CSV
- 🔗 **Random Image API** — Configurable public image endpoint
- ⚡ **API Rate Limiting** — Abuse prevention
- 🔄 **Upload Retry** — Configurable attempts, smart skip for non-retryable errors
- 📦 **Paginated Browsing** — Configurable items per page
- 💾 **KV Cloud Sync** — Persistent settings and public image list
- 🖥️ **Responsive Design** — Desktop, tablet, mobile

## 📖 Documentation

[Deployment Guide](https://docs.stoeaves.com/cf-github-imgbed/)

## 🚀 Quick Start

### Prerequisites

- Cloudflare account
- GitHub account & [Personal Access Token](https://github.com/settings/tokens)
> Make sure to check **repo** scope, otherwise the repository images cannot be accessed
- A GitHub repository (for storing images)

### 1. Deploy to Cloudflare Pages

1. Fork this repository
2. Go to [Cloudflare Dashboard](https://dash.cloudflare.com) → Workers & Pages
3. Create application → Pages → Connect to Git
4. Select the repository, configure build settings:
   - **Framework preset**: `Vue`
   - **Build command**: `npm run build`
   - **Output directory**: `dist`
5. Click Deploy

### 2. Create KV Namespace

1. Workers KV → Create namespace
2. Name it, e.g., `imgbed-kv`

### 3. Bind KV

Go to Pages project → Settings → Functions → KV namespace bindings:

| Variable name | KV namespace |
|---------------|-------------|
| `KV` | Select the namespace you just created |

### 4. Configure Environment Variables

Go to Pages project → Settings → Environment variables:

| Variable name | Required | Description |
|---------------|----------|-------------|
| `GITHUB_TOKEN` | ✅ | GitHub Personal Access Token (global default) |
| `ADMIN_PASSWORD` | ✅ | Admin password |
| `RSA_PUBLIC_KEY` | ✅ | RSA public key (base64) |
| `RSA_PRIVATE_KEY` | ✅ | RSA private key (base64) |

### 5. Generate RSA Key Pair

Copy your deployed domain, using `your-site.pages.dev` as an example.

Edit the address bar, append `/generate-keys.html`, press Enter. Click the button to generate and copy the environment variable values.

Full URL: `https://your-site.pages.dev/generate-keys.html`

### 6. First Use

1. Visit the deployed domain
2. Enter the admin password to log in
3. Go to Settings → Add Repository, fill in the information
> **Note:** Ensure there is at least one file (any file) in the repository, otherwise images cannot be uploaded
4. Start uploading images

## 📝 Changelog

- v2.0
  - UI overhaul
  - Added many new features
  - Performance optimization
  - Bug fixes
- v1.0
  - Basic features released

## 🤝 Contributing

Issues and Pull Requests are welcome. Thank you for your contribution!

Or visit [StoneLeaves Blog](https://blog.stoeaves.com/posts/cf-github-imgbed/)

## ⚠️ Notes

- Images in private repositories are served via Workers proxy, which consumes Workers free tier (100k requests/day)
- For public repositories, CDN acceleration is recommended to reduce Workers usage
- Keep the RSA private key safe and do not commit it to the repository
- KV free tier: 100k reads/day, 1k writes/day
- GitHub API rate limit: 5k requests/hour (authenticated user)

## 📝 License

This project is licensed under the [MIT License](LICENSE)

## Star History

<a href="https://www.star-history.com/?repos=Stoeaves%2FCf-Github-ImgBed&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=Stoeaves/Cf-Github-ImgBed&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=Stoeaves/Cf-Github-ImgBed&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=Stoeaves/Cf-Github-ImgBed&type=date&legend=top-left" />
 </picture>
</a>