# AGENTS.md - Ecliptical Software Inc. Website

## Overview
This repository contains the official company website for **Ecliptical Software Inc.**, a software development consulting firm specializing in Rust, Kubernetes, and Cloud-Native technologies.

## Company Information
- **Company Name**: Ecliptical Software Inc.
- **Primary Domain**: eclipticalsoftware.com
- **Secondary Domain**: ecliptical.ca
- **Contact Email**: info@eclipticalsoftware.com
- **Calendly**: https://calendly.com/ecliptical/30min

## Services Offered
1. **Instruction, Training, and Tutoring** - Personalized online instruction for Rust and Kubernetes
2. **Software Development Consulting** - Expert consulting in Rust, Kubernetes, and cloud technologies
3. **Custom Software Development** - Full-stack development services for cloud-native applications

## AWS Infrastructure

### CloudFront Distribution
- **Status**: Deployed
- **Distribution ID**: Stored as GitHub secret `CLOUDFRONT_DISTRIBUTION_ID`
- **Aliases**:
  - eclipticalsoftware.com
  - www.eclipticalsoftware.com
  - ecliptical.ca
  - www.ecliptical.ca

### S3 Bucket
- **Bucket Name**: www.eclipticalsoftware.com
- **Region**: ca-central-1 (Canada/Montreal)
- **Configuration**: Static website hosting via CloudFront (not direct S3 website hosting)

## Repository Structure
```
/
├── .github/
│   └── workflows/
│       └── deploy-aws.yml  # GitHub Action for AWS deployment
├── docs/                   # Public website assets (GitHub Pages root)
│   ├── index.html          # Main landing page
│   ├── ecliptical-md.png   # Company logo (180x180)
│   ├── favicon.ico         # Site favicon
│   └── designrush-new-logo.svg # DesignRush partner logo
├── AGENTS.md               # This file
├── LICENSE                 # Proprietary license
└── README.md               # Repository documentation
```

## Technology Stack
- **Frontend**: Bootstrap 5.3.3 (Dark theme)
- **Icons**: Bootstrap Icons 1.11.3
- **Hosting**: AWS S3 + CloudFront + GitHub Pages
- **CDN**: CloudFront (for global distribution)
- **DNS**: Both domains resolve to the same CloudFront distribution
- **SEO**: Open Graph meta tags, JSON-LD structured data

## Development Guidelines

### Deployment Process
To deploy changes to the website:

1. **Update local files** in this repository
2. **Push to GitHub** - The site is immediately available at https://ecliptical.github.io via GitHub Pages
3. **Deploy to AWS** - Use the "Deploy to AWS" GitHub Action (manual trigger) or run locally:
   ```bash
   aws s3 sync docs/ s3://www.eclipticalsoftware.com/
   aws cloudfront create-invalidation --distribution-id $CLOUDFRONT_DISTRIBUTION_ID --paths "/*"
   ```

### GitHub Actions
- **Deploy to AWS** (`deploy-aws.yml`): Manual workflow for deploying to S3 and invalidating CloudFront cache
  - Uses OIDC federation for secure, secretless AWS authentication
  - Repository secrets: `AWS_ROLE_ARN`, `CLOUDFRONT_DISTRIBUTION_ID`

### Design Principles
- Dark theme by default (`data-bs-theme="dark"`)
- Mobile-responsive design
- Bootstrap-based responsive grid layout
- Three main service areas prominently featured
- Contact CTAs (email and Calendly booking)

### Key Features
- Responsive 3-column layout for service offerings
- Bootstrap dark theme styling with smooth scrolling
- Icon-based visual design using Bootstrap Icons
- Links to external resources (Rust, Kubernetes, CNCF landscape)
- DesignRush profile integration
- Prominent CTA buttons (Email Us, Book a Call)
- Social links (GitHub, LinkedIn, X) with accessible focus states
- Open Graph tags for social media sharing
- JSON-LD structured data for SEO

## Working with AI Agents
When collaborating with AI agents on this website:

1. **Content Changes**: Update [docs/index.html](docs/index.html) for text, layout, or structural changes
2. **Assets**: Add new images or assets to the `docs/` directory
3. **Testing**: Test locally before deploying to S3
4. **Deployment**: Always invalidate CloudFront cache after S3 sync to ensure changes are visible
5. **Domains**: Remember that all four domain aliases point to the same content

## Notes
- The website uses CDN-hosted Bootstrap and Bootstrap Icons for performance (with preconnect hints)
- Canonical URL is set to https://www.eclipticalsoftware.com/
- The S3 bucket is not configured for direct website hosting; CloudFront handles all requests
- Apple touch icon and favicon are configured for mobile/browser compatibility
- GitHub Pages provides an alternative access point at https://ecliptical.github.io (updates immediately on push)
