# Bodnar Resume Theme

***A heavily modified fork of BelResumé with dynamic Tera templates***

**Forked from**: [cx48/BelResume](https://github.com/cx48/BelResume)
**This Fork**: [danielbodnar/bodnar-resume](https://github.com/danielbodnar/bodnar-resume)

> This is a forked and heavily modified version of the original BelResumé theme, featuring dynamic Tera templates and config-driven content management.

## Major Enhancements

This fork adds significant improvements over the original:

- ✅ **Dynamic Tera Templates** - All content is now managed through `config.toml` using Tera templating engine
- ✅ **Config-Driven Content** - No HTML editing required - all resume data lives in the `[extra]` section
- ✅ **Full-Width Fluid Layout** - Removed width constraints for a modern, responsive design
- ✅ **Improved Maintainability** - Update your resume by editing TOML, not HTML
- ✅ **Loop-Based Rendering** - Add/remove entries by modifying arrays in config

Powered by [Zola](https://getzola.org/). Styled with Tailwind CSS & Font Awesome

## Preview

[BelResumé](https://cx48.github.io/BelResume/) can be deployed for free using GitHub Pages or Vercel

#### Light Mode

![Light Mode](https://raw.githubusercontent.com/cx48/BelResume/refs/heads/main/static/images/light.png)

#### Dark Mode

![Dark Mode](https://raw.githubusercontent.com/cx48/BelResume/refs/heads/main/static/images/dark.png)

#### PageSpeed Insights

![PageSpeed](https://raw.githubusercontent.com/cx48/BelResume/refs/heads/main/static/images/pagespeed.png)

## Project Structure

- **config.toml**: Site metadata  
- **static/**: `css/style.css`, `js/script.js`  
- **templates/index.html**: Main layout (calls all partials)  
- **templates/partials/**: All resume sections are modular
  - `header.html`: Name, job title, contact links
  - `experience.html`: Work history (companies, roles, achievements)
  - `education.html`: Schools, degrees, specializations
  - `projects.html`: Key project summaries with tags
  - `skills.html`: Visual skill bars (adjust widths)
  - `certifications.html`: Cert title + authority + year
  - `languages.html`: Language proficiency (bars & labels)
  - `awards.html`: Award names + year + issuer

## Quick Start

1. **Install Zola**: [https://getzola.org/documentation/getting-started/installation/](https://getzola.org/documentation/getting-started/installation/) 

2. **Clone this fork**:
   ```bash
   git clone https://github.com/danielbodnar/bodnar-resume
   cd bodnar-resume
   ```

   Or use as a Zola theme:
   ```bash
   cd themes
   git clone https://github.com/danielbodnar/bodnar-resume
   ```

3. **Configure your resume**:
   Edit the `[extra]` section in `config.toml` with your resume data (see Customization Guide below)

4. **Serve locally**:
   ```bash
   zola serve
   ```

   Visit [http://127.0.0.1:1111](http://127.0.0.1:1111) to preview your resume

5. **Build static site**:
   ```bash
   zola build
   ```
   All files output to `/public`

## Deployment Guide

> Deploy to GitHub Pages

1. Run Zola build:
   ```bash
   zola build
   ```

2. Commit and push the contents of the `public/` folder to your `gh-pages` branch

3. In GitHub repo settings, enable Pages from the `/public` folder or `gh-pages` branch

4. Your site will be live at `https://yourusername.github.io/BelResume/`

> Deploy to Vercel

1. Login to [Vercel](https://vercel.com) and import your GitHub repo

2. Set **Build Command** to:
   ```bash
   zola build
   ```

3. Set **Output Directory** to:
   ```bash
   public
   ```

4. Set **Framework Preset** to `Other`

5. Click **Deploy**

Zola will build and serve from the `public/` folder automatically on every push

## Customization Guide

**⚠️ This fork uses dynamic templates!** Unlike the original BelResumé, you do **NOT** need to edit HTML files. All content is managed through `config.toml`.

### Update Your Resume Content

Edit the `[extra]` section in your site's root `config.toml`:

#### 1. **Personal Information**
```toml
[extra]
name = "John Doe"
job_title = "Senior Software Engineer"
bio = "Your professional summary"
email = "john@example.com"
phone = "(555) 123-4567"
location = "San Francisco, CA"
website = "https://johndoe.com"
```

#### 2. **Work Experience**
```toml
[[extra.experience]]
title = "Senior Developer"
company = "Tech Company"
start_date = "2020"
end_date = "Present"
achievements = [
    "Improved system performance by 30%",
    "Led team of 5 engineers"
]
```

#### 3. **Skills**
```toml
[[extra.skills]]
name = "JavaScript"
level = 95  # Percentage (0-100)
```

#### 4. **Projects/Interests**
```toml
[[extra.projects]]
title = "E-commerce Platform"
description = "Built scalable shopping platform"
technologies = ["React", "Node.js", "PostgreSQL"]
```

#### 5. **Education**
```toml
[[extra.education]]
title = "Master of CS"
institution = "Stanford University"
start_date = "2015"
end_date = "2017"
description = "GPA: 3.9 — Focus on distributed systems"
```

#### 6. **Certifications**
```toml
[[extra.certifications]]
title = "AWS Certified Architect"
description = "Amazon — 2022"
```

#### 7. **Languages**
```toml
[[extra.languages]]
name = "English"
level = "Native"
proficiency = 100  # Percentage
```

#### 8. **Awards**
```toml
[[extra.awards]]
title = "Best Hackathon Project"
description = "DefCon 2025"
```

### Template Architecture

All partials are now dynamic Tera templates:

| Template | Data Source | Type |
|----------|-------------|------|
| `header.html` | `config.extra.name`, `config.extra.email`, etc. | Variables |
| `experience.html` | `config.extra.experience` | Loop (`{% for %}`) |
| `projects.html` | `config.extra.projects` | Loop (`{% for %}`) |
| `skills.html` | `config.extra.skills` | Loop (`{% for %}`) |
| `education.html` | `config.extra.education` | Loop (`{% for %}`) |
| `certifications.html` | `config.extra.certifications` | Loop (`{% for %}`) |
| `languages.html` | `config.extra.languages` | Loop (`{% for %}`) |
| `awards.html` | `config.extra.awards` | Loop (`{% for %}`) |

## Credits & Contributing

This theme is a fork of the excellent [BelResumé](https://github.com/cx48/BelResume) by [cx48](https://github.com/cx48).

### Original Theme
- **Original Author**: cx48
- **Original Repository**: [cx48/BelResume](https://github.com/cx48/BelResume)
- **Original Issues**: [Report issues with original theme](https://github.com/cx48/BelResume/issues)

### This Fork
- **Fork Maintainer**: Daniel Bodnar
- **Fork Repository**: [danielbodnar/bodnar-resume](https://github.com/danielbodnar/bodnar-resume)
- **Fork Issues**: [Report issues with dynamic template features](https://github.com/danielbodnar/bodnar-resume/issues)

### Contributing

Contributions are welcome! If you'd like to improve the dynamic templating features or fix bugs:
1. Fork [danielbodnar/bodnar-resume](https://github.com/danielbodnar/bodnar-resume)
2. Create a feature branch
3. Submit a pull request

For issues with the original theme design or core features, please report them to the [original repository](https://github.com/cx48/BelResume/issues).
