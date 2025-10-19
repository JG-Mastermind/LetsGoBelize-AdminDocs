# LetsGoBelize Admin Onboarding Documentation

**Official admin onboarding manual for the LetsGoBelize tourism platform.**

📚 **Live Documentation**: [https://jg-mastermind.github.io/LetsGoBelize-AdminDocs/](https://jg-mastermind.github.io/LetsGoBelize-AdminDocs/)

---

## 📖 About This Repository

This repository contains comprehensive onboarding documentation for LetsGoBelize platform administrators. It covers all aspects of platform operations, from user management to payment processing.

**Note**: This is a **documentation-only repository**. The main LetsGoBelize platform codebase is maintained separately in a private repository.

---

## 🎯 Documentation Contents

### **Getting Started**
- Project Overview & ReadMe
- Roles, Permissions & RLS (Row-Level Security)
- Admin Onboarding & Invitation System

### **Core Operations**
- Tours Management
- Bookings Flow & Operations
- Payments & Stripe Connect

### **Platform Management**
- Safety Alerts Runbook
- WhatsApp Operations
- AI Assistant Governance
- Storage, Images & Files
- Analytics & Insights Dashboard

### **Security & Maintenance**
- Security & Compliance
- Backups & Disaster Recovery
- Release & Change Control
- Troubleshooting Playbook

### **Resources**
- Checklists and Templates
- Backend Flow Diagrams (Mermaid)
- API Reference (Appendix A)
- Glossary (Appendix B)

---

## 🚀 Viewing the Documentation

### **Option 1: Live Website** (Recommended)

Visit the published documentation:
```
https://jg-mastermind.github.io/LetsGoBelize-AdminDocs/
```

Features:
- Full-text search across all documentation
- Mobile-responsive design
- Dark/light mode toggle
- Expandable navigation sidebar
- Direct links to specific sections

### **Option 2: Local Preview**

Run the documentation locally on your machine:

```bash
# Install MkDocs and Material theme
pip install mkdocs mkdocs-material

# Clone this repository
git clone https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs.git
cd LetsGoBelize-AdminDocs

# Start local server
mkdocs serve

# Open in browser: http://127.0.0.1:8000
```

---

## ✏️ Contributing & Updates

### **For Documentation Updates**

This repository accepts contributions for documentation improvements:

1. **Fork this repository**
2. **Make your changes** to markdown files in `docs/` directory
3. **Test locally**: Run `mkdocs serve` to preview
4. **Submit a pull request** with clear description of changes

### **Documentation Guidelines**

- Use clear, concise language
- Include code examples where applicable
- Add screenshots for UI-related instructions
- Update navigation in `mkdocs.yml` if adding new pages
- Follow existing formatting patterns

---

## 🛠️ Technical Details

### **Built With**

- **MkDocs**: Static site generator for documentation
- **Material for MkDocs**: Modern responsive theme
- **GitHub Pages**: Free hosting for public repositories
- **GitHub Actions**: Automated deployment pipeline

### **Repository Structure**

```
LetsGoBelize-AdminDocs/
├── mkdocs.yml           # MkDocs configuration
├── README.md            # This file
├── .github/
│   └── workflows/
│       └── deploy.yml   # GitHub Actions deployment workflow
└── docs/                # Documentation source files
    ├── index.md         # Homepage
    ├── 00-15 modules    # Core documentation
    ├── appendix-*.md    # Reference materials
    ├── checklists/      # Operational checklists
    ├── quick-cards/     # Quick reference cards
    └── templates/       # Document templates
```

### **Automated Deployment**

Documentation is automatically deployed when changes are pushed to the `main` branch:

1. GitHub Actions triggers on push
2. MkDocs builds static HTML site
3. Deployment to `gh-pages` branch
4. GitHub Pages serves updated site
5. Live site updates in 2-3 minutes

---

## 🔗 Related Resources

### **LetsGoBelize Platform**

- **Main Website**: [https://letsgobelize.app](https://letsgobelize.app)
- **Main Repository**: Private (codebase not public)
- **Documentation**: This repository (public)

### **External Documentation**

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Supabase Documentation](https://supabase.com/docs)
- [Stripe Documentation](https://stripe.com/docs)

---

## 📞 Support

### **For Platform Admins**

If you're a LetsGoBelize admin with questions about platform operations:
- Refer to the [Troubleshooting Playbook](https://jg-mastermind.github.io/LetsGoBelize-AdminDocs/14-Troubleshooting-Playbook/)
- Check the [FAQ sections](https://jg-mastermind.github.io/LetsGoBelize-AdminDocs/) in relevant modules
- Contact your platform administrator

### **For Documentation Issues**

If you found an error in the documentation or have suggestions:
- [Open an issue](https://github.com/JG-Mastermind/LetsGoBelize-AdminDocs/issues) in this repository
- Submit a pull request with corrections
- Email: [Your contact email]

---

## 📄 License

This documentation is provided for LetsGoBelize platform administrators and contributors.

**Copyright © 2025 LetsGoBelize. All rights reserved.**

The LetsGoBelize platform and its proprietary AI concierge technology are protected intellectual property. This public documentation repository does not grant any rights to the underlying platform code, AI models, or commercial services.

---

## 🌟 About LetsGoBelize

LetsGoBelize is a revolutionary tourism platform featuring the world's first culturally authentic AI concierge for Belizean tourism. The platform combines:

- **Tours & Adventures**: Curated authentic Belizean experiences
- **AI Concierge**: GPT-4 powered culturally authentic travel assistant
- **Booking Management**: Seamless reservation and payment processing
- **Expert Network**: Cultural validation by community leaders
- **Multi-language Support**: English and French-Canadian interfaces

**White-label licensing available** for resorts, hotel chains, and tourism boards.

---

**Last Updated**: October 2025
**Documentation Version**: 1.0.0
**MkDocs Version**: 1.5+
**Material Theme Version**: 9.0+
