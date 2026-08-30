# Zandrel Website

<p align="center">
  <img
    src="src/Zandrel.Web/wwwroot/images/social/zandrel-social-preview.png"
    alt="Zandrel — Software solutions for your business"
    width="100%"
  />
</p>

<p align="center">
  Legacy Zandrel website built with <strong>.NET 10</strong> and <strong>Blazor WebAssembly</strong>.
</p>

<p align="center">
  <a href="https://zandrel-software.github.io/zandrel-website/">
    View Live Website
  </a>
</p>

---

## About This Repository

This repository contains the previous version of the Zandrel website.

The site was originally designed around a more formal software-business positioning and was previously served through the custom domain `zandrel.com`.

It is now preserved as a standalone GitHub Pages deployment and remains available at:

```text
https://zandrel-software.github.io/zandrel-website/
```

The `zandrel.com` domain is no longer associated with this repository.

## Original Website Purpose

This version of the website was created to communicate Zandrel's software services through a professional, business-oriented landing page.

Its original focus included:

- Professional websites
- Custom software systems
- Business process automation
- Direct project communication
- Flexible project scope
- Corrective maintenance under the original service model
- WhatsApp as the main conversion channel

The public website is written in Spanish.

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

The project intentionally avoids JavaScript frameworks, CSS frameworks, npm dependencies, authentication, and backend infrastructure unless required by future maintenance.

## Architecture

The solution contains a standalone Blazor WebAssembly application:

```text
zandrel-website/
├── .github/
│   └── workflows/
│       └── deploy.yml
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
│       │   ├── robots.txt
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

This version of Zandrel uses a restrained visual system centered around a light interface with Midnight and Iris as the primary colors.

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
https://zandrel-software.github.io/zandrel-website/
```

The deployment workflow is located at:

```text
.github/workflows/deploy.yml
```

Every push to:

```text
main
```

triggers the deployment pipeline.

The workflow can also be executed manually through `workflow_dispatch`.

The deployment process:

1. Checks out the repository
2. Configures .NET 10
3. Reads the active GitHub Pages configuration
4. Restores dependencies
5. Publishes the Blazor WebAssembly application
6. Adjusts the production base path and public URLs
7. Creates the required static-hosting files
8. Uploads the GitHub Pages artifact
9. Deploys the website

### Base Path Handling

For local development, the application keeps:

```html
<base href="/" />
```

During GitHub Pages deployment, the workflow adjusts the published artifact to use:

```html
<base href="/zandrel-website/" />
```

This allows the same source project to work correctly both locally and under the repository-specific GitHub Pages path.

## Blazor Static Assets

The project targets .NET 10 and enables HTML asset placeholder processing.

The Blazor startup script uses the .NET 10 fingerprint placeholder:

```html
<script src="_framework/blazor.webassembly#[.{fingerprint}].js"></script>
```

This allows the published application to reference the generated fingerprinted static asset correctly.

## SEO and Social Sharing

The website includes:

- Page title and meta description
- Canonical URL
- Search engine indexing directives
- Open Graph metadata
- X / Twitter Card metadata
- Social sharing preview image
- `Organization` structured data
- `WebSite` structured data
- XML sitemap
- `robots.txt`

The current canonical URL is:

```text
https://zandrel-software.github.io/zandrel-website/
```

Public SEO and social-sharing references use the GitHub Pages deployment URL, including:

- Canonical URL
- `og:url`
- `og:image`
- `twitter:image`
- Structured data identifiers and URLs
- `sitemap.xml`
- `robots.txt`

The current social preview asset is located at:

```text
src/Zandrel.Web/wwwroot/images/social/zandrel-social-preview.png
```

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

## Brand Assets

Brand assets are stored in:

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
- Public URLs are kept consistent with the active deployment
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

Live deployment:

```text
https://zandrel-software.github.io/zandrel-website/
```

---

<p align="center">
  <strong>Zandrel</strong><br />
  Previous website preserved on GitHub Pages.
</p>
