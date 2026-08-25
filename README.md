# Zandrel Website

<p align="center">
  <img
    src="src/Zandrel.Web/wwwroot/images/social/zandrel-social-preview.png"
    alt="Zandrel — Software solutions for your business"
    width="100%"
  />
</p>

<p align="center">
  Official website for <strong>Zandrel</strong>, built with .NET 10 and Blazor WebAssembly.
</p>

<p align="center">
  <a href="https://zandrel.com/">
    View Live Website
  </a>
</p>

---

## About Zandrel

Zandrel creates software solutions around real business needs.

The company focuses on making technology easier to understand, accessible to businesses with different budgets, and supported by clear, personal communication throughout the project.

Current service areas include:

- Professional websites
- Custom software systems
- Business process automation
- Corrective maintenance for delivered solutions

The public website is currently written in Spanish and designed primarily for businesses, entrepreneurs, independent professionals, and small companies.

## Website Goals

The website is designed to communicate Zandrel's value proposition without unnecessary technical complexity.

Its main goals are to:

- Explain services in clear, business-oriented language
- Help potential clients understand how Zandrel works
- Communicate that project scope can be adapted to real needs and viable budgets
- Emphasize direct, personal attention without bots
- Explain the included corrective maintenance model clearly
- Convert interested visitors through WhatsApp
- Present Zandrel as a professional, modern, and trustworthy software brand

## Tech Stack

| Area | Technology |
| --- | --- |
| Framework | .NET 10 |
| Frontend | Blazor WebAssembly |
| Language | C# |
| UI | Razor Components |
| Styling | Custom CSS |
| Hosting | GitHub Pages |
| CI/CD | GitHub Actions |

The project intentionally avoids JavaScript frameworks, CSS frameworks, npm dependencies, authentication, and backend infrastructure unless they become necessary in the future.

## Architecture

The solution currently contains a standalone Blazor WebAssembly application:

```text
zandrel-website/
├── .github/
│   └── workflows/
│       └── deploy-pages.yml
│
├── src/
│   └── Zandrel.Web/
│       ├── Components/
│       │   └── Home/
│       ├── Constants/
│       ├── Layout/
│       ├── Pages/
│       ├── wwwroot/
│       │   ├── css/
│       │   ├── images/
│       │   │   ├── brand/
│       │   │   └── social/
│       │   ├── index.html
│       │   └── sitemap.xml
│       ├── App.razor
│       ├── Program.cs
│       └── Zandrel.Web.csproj
│
├── README.md
└── Zandrel.slnx
```

## Landing Page Structure

The current landing page follows this structure:

```text
Header
└── Hero
    └── Why Zandrel
        └── Services
            └── Budget-focused solutions
                └── How we work
                    └── Who we work with
                        └── About Zandrel
                            └── Included maintenance
                                └── Customer commitments
                                    └── Final CTA
                                        └── Footer
```

The experience is intentionally focused on a single conversion channel: WhatsApp.

## Design System

Zandrel uses a restrained visual system centered around a light interface with Midnight and Iris as the primary brand colors.

### Core Colors

| Token | Value |
| --- | --- |
| Midnight | `#151B2D` |
| Iris | `#6657E8` |
| Iris Hover | `#5748D7` |
| Iris Light | `#EEEAFE` |
| Background | `#F8F9FC` |
| Surface | `#FFFFFF` |
| Text | `#171A24` |
| Muted Text | `#697386` |
| Border | `#E3E6ED` |

The visual direction is intended to feel:

- Modern
- Professional
- Clear
- Technology-oriented without being overly technical
- Accessible without appearing inexpensive
- Clean rather than visually overloaded

## Local Development

### Requirements

Install the .NET 10 SDK.

Verify the installation:

```powershell
dotnet --version
```

The installed version should be compatible with:

```text
10.0.x
```

### Clone the Repository

```powershell
git clone https://github.com/zandrel-software/zandrel-website.git
```

Navigate to the repository:

```powershell
cd zandrel-website
```

### Restore Dependencies

```powershell
dotnet restore ./src/Zandrel.Web/Zandrel.Web.csproj
```

### Run the Application

```powershell
dotnet run --project ./src/Zandrel.Web/Zandrel.Web.csproj
```

Alternatively, open:

```text
Zandrel.slnx
```

in Visual Studio and run `Zandrel.Web`.

## Production Build

Create a Release build with:

```powershell
dotnet publish ./src/Zandrel.Web/Zandrel.Web.csproj --configuration Release
```

The application is a standalone Blazor WebAssembly site and produces static assets that can be served without an ASP.NET Core backend.

## Deployment

The website is deployed automatically to GitHub Pages through GitHub Actions.

Current production URL:

```text
https://zandrel.com/
```

The deployment workflow is located at:

```text
.github/workflows/deploy-pages.yml
```

Every push to:

```text
main
```

triggers the deployment pipeline.

The workflow:

1. Checks out the repository
2. Configures .NET 10
3. Configures GitHub Pages
4. Restores dependencies
5. Publishes the Blazor WebAssembly application
6. Adjusts the production base path for the GitHub Pages project site
7. Creates the required static-hosting files
8. Uploads the Pages artifact
9. Deploys the website

The source `index.html` intentionally keeps:

```html
<base href="/" />
```

for local development.

The deployment workflow changes the published copy to:

```html
<base href="/" />
```

for GitHub Pages.

## Blazor Static Assets

The project targets .NET 10 and enables HTML asset placeholder processing:

```xml
<OverrideHtmlAssetPlaceholders>true</OverrideHtmlAssetPlaceholders>
```

The Blazor startup script therefore uses the .NET 10 fingerprint placeholder:

```html
<script src="_framework/blazor.webassembly#[.{fingerprint}].js"></script>
```

This allows the published application to reference the generated fingerprinted static asset correctly.

## SEO and Social Sharing

The website currently includes:

- Page title and meta description
- Canonical URL
- Search engine indexing directives
- Open Graph metadata
- X / Twitter Card metadata
- Social sharing preview image
- `Organization` structured data
- `WebSite` structured data
- XML sitemap

The current social preview asset is located at:

```text
src/Zandrel.Web/wwwroot/images/social/zandrel-social-preview.png
```

The SEO configuration currently references the temporary GitHub Pages URL.

When Zandrel moves to a custom domain, the following production references must be updated together:

- Canonical URL
- `og:url`
- `og:image`
- `twitter:image`
- Structured data URLs
- `sitemap.xml`
- GitHub Pages custom-domain configuration

## Responsive Design

The website is designed for:

- Desktop
- Laptop
- Tablet
- Mobile
- Small mobile viewports

Responsive behavior is implemented with custom CSS and does not depend on a third-party UI framework.

The mobile experience includes:

- Full-width responsive layout
- Fullscreen navigation
- Mobile-safe spacing
- Responsive Hero composition
- Touch-friendly CTAs
- Responsive business content
- Reduced visual decoration when necessary for clarity

## Accessibility

The project includes foundational accessibility considerations such as:

- Semantic headings and sections
- ARIA labels where appropriate
- Visible keyboard focus states
- Decorative content hidden from assistive technologies
- Reduced-motion support
- Accessible navigation controls
- Descriptive image alternatives where required

Accessibility will continue to be reviewed as the website evolves.

## Brand Assets

Official brand assets are stored in:

```text
src/Zandrel.Web/wwwroot/images/brand/
```

Current variants include:

```text
zandrel-logo-horizontal-transparent.png
zandrel-logo-horizontal-white.png
zandrel-logo-horizontal-black.png

zandrel-mark-transparent.png
zandrel-mark-white.png
zandrel-mark-black.png
```

## Development Conventions

The project follows these conventions:

- Technical naming is written in English
- Public website content is written in Spanish
- C# nullable reference types are enabled
- Implicit usings are enabled
- Components use scoped CSS when appropriate
- Business and brand URLs are centralized instead of duplicated
- Unnecessary dependencies are avoided
- Changes should remain focused and minimal
- Git history follows Conventional Commits

Examples:

```text
feat: add new website section
fix: correct mobile navigation behavior
refactor: simplify hero visual composition
chore: update brand assets
ci: update github pages actions
```

## Repository

Organization:

```text
zandrel-software
```

Repository:

```text
zandrel-website
```

---

<p align="center">
  <strong>Zandrel</strong><br />
  Technology built around real business needs.
</p>