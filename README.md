# Andrisaie Enterprises

Landing page for Andrisaie Enterprises.

## Quickstart

```powershell
# Install dependencies
bundle install

# Build the site
bundle exec jekyll build

# Serve locally with live reload
bundle exec jekyll serve
```

Open http://localhost:4000 in your browser.

## Setup (Windows with PowerShell & Scoop)

### Prerequisites

1. **Install Scoop** (if not already installed):
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Force
Invoke-RestMethod get.scoop.sh | Invoke-Expression
```

2. **Install Ruby via Scoop**:
```powershell
scoop install ruby
scoop install msys2
```

3. **Install Ruby Development Toolchain**:

After installing Ruby, you need to install the MSYS2 development toolchain to compile native gem extensions.

```powershell
ridk install 3
```

This will:
- Set up MSYS2 package manager
- Install make, gcc, and other build tools
- Configure the Ruby environment

**Important**: If you skip this step, you'll encounter errors like `No such file or directory - make` when running `bundle install`.

4. **Install Bundler**:
```powershell
gem install bundler
```

5. **Install Jekyll & Dependencies**:
```powershell
bundle install
```

This will install ~99 gems including Jekyll 3.10.0 and all GitHub Pages dependencies.

### Common Issues & Solutions

#### Issue: `make failedNo such file or directory - make`

**Cause**: MSYS2 development toolchain not installed.

**Solution**: Run `ridk install 3` to install the development toolchain (make, gcc, etc.).

#### Issue: `Platform :mingw, :x64_mingw, :mswin is deprecated`

**Note**: This is just a deprecation warning and can be safely ignored. The build will still work.

#### Issue: Gem version conflicts with github-pages

**Cause**: Trying to use Jekyll 4.x with github-pages gem (which requires Jekyll 3.x).

**Solution**: The Gemfile uses `gem 'github-pages'` which automatically resolves to GitHub Pages compatible versions. Don't manually specify Jekyll version.

## Build & Serve

### Build Once

Builds the site to `_site/` directory:

```powershell
bundle exec jekyll build
```

### Build with Clean

Remove previous build before building:

```powershell
Remove-Item -Recurse -Force _site
bundle exec jekyll build
```

### Serve with Live Reload

Serves at http://localhost:4000 and auto-rebuilds on file changes:

```powershell
bundle exec jekyll serve
```

Or with live reload (refreshes browser automatically):

```powershell
bundle exec jekyll serve --livereload
```

### Serve on Different Port

```powershell
bundle exec jekyll serve --port 4001
```

## Project Structure

```
├── _config.yml           # Site configuration
├── _data/
│   └── brands.yml        # Brand data (logos, descriptions, URLs)
├── _includes/            # Reusable components
│   ├── head.html         # Meta tags, stylesheets
│   ├── header.html       # Hero section with social links
│   └── footer.html       # Footer with scripts
├── _layouts/
│   └── default.html      # Main page layout
├── _sass/                # SCSS partials
│   ├── uno.scss          # Main theme
│   ├── timeline.scss     # Timeline component
│   ├── animate.scss      # Animations
│   ├── monokai.scss      # Code highlighting
│   └── tables.scss       # Table styles
├── css/
│   └── main.scss         # Main stylesheet (imports all partials)
├── js/
│   ├── main.js           # Panel animations & mobile menu
│   └── github_api.js     # GitHub API integration
├── images/               # Image assets
│   ├── logo.png
│   ├── btph_logo.png
│   ├── nca_logo.png
│   └── favicons/
└── index.html            # Homepage (timeline layout)
```

## Customization

### Add a New Brand

Edit `_data/brands.yml`:

```yaml
- name: Your Brand Name
  desc: Brief description
  img: '/images/yourbrand_logo.png'
  url: https://www.yourbrand.com/
```

### Update Site Information

Edit `_config.yml`:

```yaml
title: Your Site Title
description: Your description
url: 'https://www.yoursite.com'
author:
  name: Your Name
  email: your@email.com
  github_username: yourusername
```

### Change Colors

Edit `_sass/uno.scss` - look for color hex codes:
- Primary: `#e25440` (coral red)
- Hover: `#b9301c` (dark red)
- Selection: `#fae3df` (light pink)

### Update Hero Image

Edit `_includes/header.html`, line 5:

```html
<header class="panel-cover" style="background-image: url(YOUR_IMAGE_URL)">
```

## Deployment

### GitHub Pages (Automatic)

Simply push to the `main` branch:

```powershell
git add .
git commit -m "Update site"
git push origin main
```

GitHub Pages automatically builds and deploys your site using the exact same `github-pages` gem.

### Custom Domain

1. Add `CNAME` file with your domain
2. Configure DNS:
   - A records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Or CNAME record to `yourusername.github.io`

## Technologies

- **Jekyll 3.10.0** - Static site generator
- **GitHub Pages** - Hosting & automatic deployment
- **SCSS** - Styling
- **jQuery** - DOM manipulation
- **Font Awesome 6.7.2** - Icons
- **Liquid** - Template engine

## License

See [LICENSE](LICENSE) file.
