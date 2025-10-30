> **📢 Repository Information**  
> This repository is named `UPDATED-WEBSITE-BUILD-REPO-MAIN.-v.0.5 on GitHub.  
> Access it at: https://github.com/573clt88-oss/UPDATED-WEBSITE-BUILD-REPO-MAIN.v.0.5 
> GitHub Pages URL: https://573clt88-oss.github.io/UPDATED-WEBSITE-BUILD-REPO-MAIN.v.0.5'

**🚀 Want to get started quickly? See [QUICKSTART.md](./QUICKSTART.md) for a 15-minute setup guide!**

**🔧 Having deployment issues? See [GITHUB_PAGES_FIX.md](./GITHUB_PAGES_FIX.md) for GitHub Pages deployment troubleshooting.**

Digital Store-6527 is an online storefront template for selling digital products (downloads, licenses, subscriptions). This repository contains the website source and build scripts for the updated website build.

## Overview

A simple, production-ready starter for a digital storefront with product listings, checkout flow, and admin tools for managing downloads and orders.

## Key features
- Product catalog (digital downloads)
- Cart & checkout integration with Stripe
- Order history and simple admin panel
- User authentication and registration
- Promotional campaigns (e.g., "First 10" users)
- Email automation (welcome emails, order confirmations)
- Static site build and server API for downloads
- Download limits (3 downloads per product)
- Secure payment processing
- Basic analytics and email notifications (configurable)

## Tech stack (repo composition)
- **Frontend**: React 19 with Tailwind CSS and shadcn/ui components
- **Backend**: FastAPI (Python) with async support
- **Database**: MongoDB (local or MongoDB Atlas)
- **Payments**: Stripe Checkout
- **Email**: Omnisend.com Transactional
- **Security**: JWT authentication, BCrypt password hashing, rate limiting

## Quick start

### 🎯 For Beginners: Use the Setup Script

```bash
git clone https://github.com/573clt88-oss/UPDATED-WEBSITE-BUILD-REPO.git
cd UPDATED-WEBSITE-BUILD-REPO-MAIN.-v.0.5
./setup.sh
```

Then follow the on-screen instructions!

### 📚 For Detailed Instructions

See [QUICKSTART.md](./QUICKSTART.md) for comprehensive step-by-step setup guide.

## Prerequisites
- git
- Node.js (v14+)
- npm or yarn
- Python 3.8+
- MongoDB (local or MongoDB Atlas account)

## Manual Setup

If you prefer to set up manually instead of using the automated script:

### Clone

    git clone https://github.com/573clt88-oss/UPDATED-WEBSITE-BUILD-REPO.git
    cd UPDATED-WEBSITE-BUILD-REPO-MAIN.-v.0.5

### Install (frontend)

    cd frontend
    npm install

### Install (backend)

    cd ../backend
    python3 -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt

### Configure Environment Variables

Backend (`backend/.env`):
```env
MONGO_URL=mongodb://localhost:27017
DB_NAME=digitalstore_dev
SECRET_KEY=your-secret-key
CORS_ORIGINS=http://localhost:3000
STRIPE_API_KEY=sk_test_your_test_key

```

Frontend (`frontend/.env`):
```env
REACT_APP_BACKEND_URL=http://localhost:8001
```

See `.env.example` files in both directories for complete configuration options.

### Seed Database (Optional)

    cd backend
    source venv/bin/activate
    python seed_data.py

### Run locally (development)

**Backend:**

    cd backend
    source venv/bin/activate
    uvicorn server:app --host 0.0.0.0 --port 8001 --reload

**Frontend:**

    cd frontend
    npm start

Visit http://localhost:3000 to see your store!

## Build for Production

    # build frontend static assets
    cd frontend
    npm run build

The production build will be in `frontend/build/` directory.

## Deployment

### GitHub Pages (Free Hosting)
This repository is configured for automatic deployment to GitHub Pages:
- **Live URL**: https://573clt88-oss.github.io/UPDATED-WEBSITE-BUILD-REPO-MAIN-v.0.5
- **Deployment**: Automatic on push to `main` branch
- **Configuration**: See [GITHUB_PAGES_FIX.md](./GITHUB_PAGES_FIX.md) for details

When you push to the `main` branch, GitHub Actions will automatically:
1. Install dependencies
2. Build the React app
3. Deploy to GitHub Pages

**Note**: The backend API is not included in GitHub Pages deployment. This is frontend-only. For full-stack deployment, see the guides below.

### Other Deployment Options

See our comprehensive deployment guides:
- **[GITHUB_PAGES_FIX.md](./GITHUB_PAGES_FIX.md)** - GitHub Pages deployment guide and troubleshooting
- **[QUICKSTART.md](./QUICKSTART.md)** - Quick local setup (15 minutes)
- **[DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md)** - Full production deployment
- **[PRODUCTION_CHECKLIST.md](./PRODUCTION_CHECKLIST.md)** - Pre-launch checklist
- **[LAUNCH_GUIDE.md](./LAUNCH_GUIDE.md)** - Step-by-step launch guide

**Recommended hosts:**
- Frontend: Vercel, Netlify, or GitHub Pages
- Backend: Heroku, Railway, or DigitalOcean
- Database: MongoDB Atlas (free tier available)

## Testing

### Test with Stripe

Use these test cards in checkout:
- **Success**: `4242 4242 4242 4242`
- **Decline**: `4000 0000 0000 0002`

Any future expiry date and any CVC will work.

### API Documentation

When backend is running, visit:
- Swagger UI: http://localhost:8001/docs
- ReDoc: http://localhost:8001/redoc

## Project Structure

```
UPDATED-WEBSITE-BUILD-REPO/
├── frontend/               # React frontend application
│   ├── public/            # Static files
│   ├── src/
│   │   ├── components/    # React components
│   │   ├── context/       # React context (auth, cart)
│   │   ├── services/      # API services
│   │   └── App.js         # Main app component
│   ├── package.json       # Frontend dependencies
│   └── .env.example       # Environment variables template
│
├── backend/               # FastAPI backend application
│   ├── server.py          # Main FastAPI application
│   ├── database.py        # MongoDB connection and queries
│   ├── models.py          # Pydantic models
│   ├── auth.py            # Authentication logic
│   ├── security.py        # Security middleware
│   ├── email_service.py   # Email automation
│   ├── stripe_integration.py  # Stripe payment wrapper
│   ├── seed_data.py       # Database seeding script
│   ├── requirements.txt   # Python dependencies
│   └── .env.example       # Environment variables template
│
├── QUICKSTART.md          # Quick setup guide (START HERE!)
├── DEPLOYMENT_GUIDE.md    # Production deployment guide
├── PRODUCTION_CHECKLIST.md # Pre-launch checklist
├── LAUNCH_GUIDE.md        # Step-by-step launch
├── setup.sh               # Automated setup script
└── README.md              # This file
```

## Environment variables

**Backend (.env):**
- `MONGO_URL` - MongoDB connection string
- `DB_NAME` - Database name
- `SECRET_KEY` - JWT secret key (generate with `python -c "import secrets; print(secrets.token_urlsafe(32))"`)
- `CORS_ORIGINS` - Comma-separated list of allowed origins
- `STRIPE_API_KEY` - Stripe API key (test or live)
- 

**Frontend (.env):**
- `REACT_APP_BACKEND_URL` - Backend API URL

**⚠️ Important:** Never commit .env files to version control!

## Features Overview

### For Customers
- Browse digital products
- Add to cart and checkout securely
- Register account or checkout as guest
- Download purchased products (up to 3 times each)
- View order history
- Access free course module
- Contact support

### For Store Owners
- Product management via database
- Secure payment processing with Stripe
- Automated email notifications
- Promotional campaigns (e.g., "First 10" users)
- Order tracking and management
- Download limit enforcement
- User authentication and registration

### Security Features
- BCrypt password hashing
- JWT token authentication
- Rate limiting (100 requests/60 seconds)
- CORS protection
- Security headers
- Input validation and sanitization
- SQL injection prevention
- XSS protection

## Contributing

We welcome contributions! Here's how to get started:

1. **Report Issues**: Use our [issue templates](https://github.com/573clt88-oss/UPDATED-WEBSITE-BUILD-REPO-MAIN.v.0.5/issues/new/choose) to report bugs, request features, or suggest improvements
2. Fork the repo
3. Create a branch: `git checkout -b feature/your-feature`
4. Make your changes
5. Test thoroughly
6. Commit and open a PR with a short description

When creating issues, please use the appropriate template:
- 🐛 **Bug Report** - For reporting bugs or unexpected behavior
- ✨ **Feature Request** - For proposing new features
- 🔧 **Enhancement** - For improving existing features
- 📖 **Documentation** - For documentation issues or improvements
- 📋 **Task/Chore** - For maintenance and non-feature work

## Roadmap ideas

- [ ] Admin dashboard UI
- [ ] Payment provider integrations (PayPal, Apple Pay)
- [ ] Advanced analytics and A/B testing
- [ ] Internationalization & localization
- [ ] Product reviews and ratings
- [ ] Wishlist functionality
- [ ] Affiliate program
- [ ] Mobile app
- [ ] Newsletter campaigns
- [ ] Customer reviews

## Support

- **Setup Issues**: See [QUICKSTART.md](./QUICKSTART.md)
- **Deployment**: See [DEPLOYMENT_GUIDE.md](./DEPLOYMENT_GUIDE.md)
- **API Documentation**: http://localhost:8001/docs (when running)
- **Stripe Help**: https://stripe.com/docs
- **MongoDB Help**: https://docs.mongodb.com

## License

MIT — change as needed.

## Contact

Owner: 573clt88-oss

---

**Ready to start?** 🚀 See [QUICKSTART.md](./QUICKSTART.md) for setup instructions!
