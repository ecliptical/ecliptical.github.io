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
- **Distribution ID**: E3GL3C9TLDW9XN
- **CloudFront Domain**: d1eydgl8kp3bbn.cloudfront.net
- **Status**: Deployed
- **Aliases**:
  - eclipticalsoftware.com
  - www.eclipticalsoftware.com
  - ecliptical.ca
  - www.ecliptical.ca

### S3 Bucket
- **Bucket Name**: www.eclipticalsoftware.com
- **Region**: ca-central-1 (Canada/Montreal)
- **Origin**: www.eclipticalsoftware.com.s3.amazonaws.com
- **Configuration**: Static website hosting via CloudFront (not direct S3 website hosting)

## Repository Structure
```
/
├── index.html              # Main landing page
├── ecliptical-md.png       # Company logo (180x180)
├── favicon.ico             # Site favicon
├── designrush-new-logo.svg # DesignRush partner logo
└── AGENTS.md              # This file
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
3. **Sync to S3 bucket**:
   ```bash
   aws s3 sync . s3://www.eclipticalsoftware.com/ --exclude ".git/*" --exclude "AGENTS.md"
   ```
4. **Invalidate CloudFront cache**:
   ```bash
   aws cloudfront create-invalidation --distribution-id E3GL3C9TLDW9XN --paths "/*"
   ```

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

1. **Content Changes**: Update [index.html](index.html) for text, layout, or structural changes
2. **Assets**: Add new images or assets to the root directory
3. **Testing**: Test locally before deploying to S3
4. **Deployment**: Always invalidate CloudFront cache after S3 sync to ensure changes are visible
5. **Domains**: Remember that all four domain aliases point to the same content

## Notes
- The website uses CDN-hosted Bootstrap and Bootstrap Icons for performance (with preconnect hints)
- Canonical URL is set to https://www.eclipticalsoftware.com/
- The S3 bucket is not configured for direct website hosting; CloudFront handles all requests
- Apple touch icon and favicon are configured for mobile/browser compatibility
- GitHub Pages provides an alternative access point at https://ecliptical.github.io (updates immediately on push)
