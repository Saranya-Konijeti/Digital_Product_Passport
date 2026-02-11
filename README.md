# 🌿 EcoPassport - Sustainable Product Tracking & Verification Platform

A comprehensive web application for tracking, verifying, and promoting sustainable products through QR code scanning, environmental metrics, and blockchain-based verifiable credentials.

## 📋 Overview

EcoPassport transforms product transparency by enabling consumers and manufacturers to:
- **Scan & Track** products via QR codes to view complete environmental data
- **Verify Authenticity** using tamper-proof verifiable credentials
- **Compare Impact** across similar products with detailed environmental metrics
- **Monitor Supply Chains** from production to end-of-life
- **Calculate Carbon Footprint** and make sustainable choices
- **Earn Rewards** through loyalty programs for eco-friendly purchases

##  Key Features

###  Consumer Features
- **QR Code Scanner** - Real-time product scanning with computer vision
- **Product Details** - Comprehensive environmental, certifications, and supply chain data
- **Carbon Calculator** - Calculate your personal carbon footprint
- **Product Comparison** - Side-by-side analysis of similar products
- **Loyalty Rewards** - Earn points for sustainable purchases
- **Community Challenges** - Participate in environmental impact challenges
- **Recycling Finder** - Locate nearby recycling centers
- **Reviews & Ratings** - Community-driven product feedback

###  Manufacturer Features
- **Secure Dashboard** - Manage products, certifications, and supply chain data
- **QR Generation** - Create traceable product codes
- **Version Tracking** - Maintain complete product history
- **Certifications Management** - Upload and verify environmental certifications
- **Supply Chain Input** - Record material sources and manufacturing details
- **End-of-Life Guidance** - Provide recycling and disposal instructions
- **Analytics** - Monitor product performance and consumer interactions
- **Audit Logs** - Complete transparency through event tracking

###  Enterprise Features
- **Verifiable Credentials** - W3C-compliant blockchain credentials
- **Trust System** - Reputation tracking for manufacturers
- **Validation System** - Multi-layer verification with evidence trails
- **Audit Logging** - Complete event history with timestamps
- **Version Control** - Full product revision history

##  Technology Stack

- **Frontend**: React 18 + TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **UI Components**: Shadcn UI + Radix UI
- **Form Handling**: React Hook Form + Zod
- **Charts/Analytics**: Recharts
- **QR Scanning**: jsQR + html5-QR-code
- **Database**: Supabase (PostgreSQL)
- **Testing**: Vitest

##  Getting Started

### Prerequisites
- Node.js 18+ (install via [nvm](https://github.com/nvm-sh/nvm))
- Bun or npm package manager

### Installation

```bash
# Clone the repository
git clone <YOUR_GIT_URL>
cd eco-pass-scan-clone

# Install dependencies
npm install
# or
bun install

# Start development server
npm run dev

# Open http://localhost:5173 in your browser
```

### Build for Production

```bash
npm run build      # Build optimized version
npm run preview    # Preview production build locally
```

### Testing & Linting

```bash
npm test           # Run tests once
npm run test:watch # Run tests in watch mode
npm run lint       # Check code quality with ESLint
```

## 📁 Project Structure

```
src/
├── pages/              # Page components (QR scanner, dashboard, etc.)
├── components/
│   ├── products/       # Product-related components
│   ├── ui/            # Shadcn UI components
│   ├── QRScanner.tsx  # QR code scanning
│   ├── SupplyChainTracker.tsx
│   └── ProductReviews.tsx
├── hooks/             # Custom React hooks
├── lib/
│   ├── types.ts       # TypeScript type definitions
│   ├── utils.ts       # Utility functions
│   └── verifiable-credentials.ts
├── integrations/
│   └── supabase/      # Database configuration
└── test/              # Test files
```

## 🗄️ Database Schema

The application uses 11 tables for complete product lifecycle management:
- **products** - Core product information
- **product_versions** - Version history tracking
- **environmental_data** - Carbon, water, waste metrics
- **supply_chain** - Manufacturing and sourcing details
- **certifications** - Environmental certificates (ISO, FSC, etc.)
- **end_of_life** - Recycling and disposal guidance
- **reviews** - Consumer ratings and feedback
- **manufacturers** - Business details and trust metrics
- **credentials** - Verifiable credentials storage
- **audit_logs** - Event tracking and compliance
- **validations** - Verification records with evidence trails

## 🔧 Configuration

### Environment Variables
Create a `.env.local` file with:
```
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_anon_key
```

### Tailwind CSS & UI Components
- Configured in `tailwind.config.ts`
- Components defined in `components.json`
- Uses Radix UI as the underlying component library

## 📊 Available Pages

| Page | Route | Purpose |
|------|-------|---------|
| Dashboard | `/` | Home and overview |
| Scan QR | `/scan` | Real-time QR code scanning |
| Product Detail | `/product/:id` | Full product information |
| Compare Products | `/compare` | Side-by-side analysis |
| Carbon Calculator | `/calculator` | Personal footprint tracking |
| Browse Products | `/browse` | Product catalog |
| Recycling Finder | `/recycling` | Locate recycling centers |
| Loyalty Rewards | `/rewards` | Track points and rewards |
| Community Challenges | `/challenges` | Environmental activities |
| Manufacturer Auth | `/auth/manufacturer` | Login for businesses |
| Manufacturer Dashboard | `/manufacturer` | Business admin panel |
| Analytics | `/analytics` | Performance insights |
| Impact Visualizer | `/impact` | Environmental data visualization |

## 🤝 Contributing

Local development workflow:
1. Create a feature branch
2. Make changes and test locally with `npm run dev`
3. Run tests: `npm test`
4. Lint code: `npm run lint`
5. Build: `npm run build`
6. Commit and push changes

## 📝 License

This project is proprietary. All rights reserved.

## 📞 Support

For issues, questions, or feature requests, please contact your development team.
- Edit files directly within the Codespace and commit and push your changes once you're done.

## What technologies are used for this project?

This project is built with:

- Vite
- TypeScript
- React
- shadcn-ui
- Tailwind CSS
