# Ecliptical Software Inc. Website

Official company website for **Ecliptical Software Inc.** - a software development consulting firm specializing in Rust, Kubernetes, and Cloud-Native technologies.

## 🌐 Live Sites

- **Primary**: [eclipticalsoftware.com](https://www.eclipticalsoftware.com)
- **Secondary**: [ecliptical.ca](https://www.ecliptical.ca)
- **GitHub Pages**: [ecliptical.github.io](https://ecliptical.github.io)

## 🛠 Services

- **Instruction, Training, and Tutoring** - Personalized online instruction for Rust and Kubernetes
- **Software Development Consulting** - Expert consulting in Rust, Kubernetes, and cloud technologies
- **Custom Software Development** - Full-stack development services for cloud-native applications

## 📁 Repository Structure

```
/
├── docs/                   # Public website assets (GitHub Pages root)
│   ├── index.html          # Main landing page
│   ├── ecliptical-md.png   # Company logo
│   ├── favicon.ico         # Site favicon
│   └── designrush-new-logo.svg
├── AGENTS.md               # AI agent collaboration guidelines
└── README.md               # This file
```

## 🚀 Deployment

The website is hosted on:
- **GitHub Pages** - Automatically deployed from the `/docs` folder on push
- **AWS CloudFront + S3** - For custom domains with global CDN

### Deploy to AWS

```bash
# Sync to S3
aws s3 sync docs/ s3://www.eclipticalsoftware.com/

# Invalidate CloudFront cache
aws cloudfront create-invalidation --distribution-id E3GL3C9TLDW9XN --paths "/*"
```

## 📧 Contact

- **Email**: [info@eclipticalsoftware.com](mailto:info@eclipticalsoftware.com)
- **Book a Call**: [Calendly](https://calendly.com/ecliptical/30min)

## 📄 License

© 2005 - 2026 Ecliptical Software Inc. All rights reserved.
