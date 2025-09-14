# Raghu Engineering College - Campus Lost & Found Portal

A comprehensive lost and found portal designed specifically for Raghu Engineering College and other Vizag colleges.

## Features

- 🏫 **College-Based Access Control**: Each college only sees items from their own campus
- 🔒 **Secure Data Isolation**: Complete privacy between different colleges
- 📱 **Responsive Design**: Works on all devices (mobile, tablet, desktop)
- 📧 **Email Notifications**: Automatic notifications when items are found
- 📊 **Excel Database**: All data stored in Excel format for easy management
- 🎯 **Raghu Engineering College Focus**: Optimized for REC students

## Quick Start

### Local Development
1. Install dependencies: `npm install`
2. Start server: `npm start`
3. Open: `http://localhost:3000`

### Online Deployment

#### Option 1: Railway (Recommended)
1. Push code to GitHub
2. Connect Railway to your GitHub repo
3. Deploy automatically
4. Get your live URL

#### Option 2: Netlify (Static + Serverless)
1. Push code to GitHub
2. Connect Netlify to your repo
3. Deploy with build command: `npm install && npm start`

## College Support

### Primary Colleges
- Raghu Engineering College
- Raghu Institute of Technology
- Raghu College of Engineering

### Other Vizag Colleges
- Andhra University
- GITAM University
- IIIT Vizag
- ANITS
- GVP College of Engineering
- And many more...

## Technology Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Backend**: Node.js, Express.js
- **Database**: Excel (XLSX)
- **Email**: Nodemailer
- **Hosting**: Railway/Netlify

## API Endpoints

- `GET /api/items` - Get all items
- `GET /api/items/college/:college` - Get items for specific college
- `POST /api/items/lost` - Add lost item
- `POST /api/items/found` - Add found item
- `PUT /api/items/:type/:id` - Update item status
- `POST /api/finder-details` - Save finder details
- `POST /api/item-claim` - Submit item claim

## Support

For technical support or questions, please contact the development team.

## License

MIT License - Feel free to use and modify for your college.