# QR Lost & Found

A complete lost and found solution using QR codes to help reunite people with their lost items. The system consists of a mobile app for item registration and a web app for QR scan landing pages.

## 🎯 Overview

QR Lost & Found makes it easy to return lost items to their owners. Users register their valuables with QR code stickers, and if someone finds a lost item, they simply scan the QR code with their phone camera to help return it through secure drop-off locations.

## 📁 Project Structure

```
qr_lost_found/
├── mobile/          # React Native mobile app (Expo)
│   ├── app/        # App screens & routing
│   ├── screens/    # Screen components
│   └── components/ # Reusable components
│
├── web/            # Next.js web application
│   ├── app/        # Pages & API routes
│   │   ├── found/     # QR scan landing page
│   │   ├── register/  # Registration page
│   │   └── api/       # API endpoints
│   └── public/     # Static assets
│
└── README.md       # This file
```

## 🚀 Quick Start

### Prerequisites
- Node.js 18 or higher
- npm or yarn
- Expo CLI (for mobile development)

### Mobile App Setup

```bash
cd mobile
npm install
npm start
```

See [mobile/README.md](mobile/README.md) for detailed instructions.

### Web App Setup

```bash
cd web
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view.

See [web/README.md](web/README.md) for detailed instructions.

## 🌟 Features

### Mobile App
- 📱 Register items with QR codes
- 📷 Scan QR codes to report found items
- 📋 Manage all registered items
- 🔔 Push notifications when items are found
- 📊 Track item status

### Web App
- 🌐 QR code scan landing pages
- 📝 Web-based item registration
- 📍 Secure drop-off location system
- ⏱️ 7-day pickup countdown
- 🔒 Privacy-protected owner information

## 💡 How It Works

1. **Register**: Attach a QR code sticker to your item and register it in the mobile app
2. **Scan**: If someone finds your item, they scan the QR code with their phone camera
3. **Report**: The finder selects a secure drop-off location (library, police station, etc.)
4. **Notify**: You receive a notification that your item has been found
5. **Reunite**: Pick up your item from the drop-off location within 7 days

## 🛠️ Tech Stack

### Mobile App
- React Native + Expo
- Expo Router (file-based routing)
- React Navigation
- Expo Camera & Barcode Scanner
- Expo Notifications
- AsyncStorage

### Web App
- Next.js 16 (App Router)
- TypeScript
- Tailwind CSS
- Vercel (deployment)

## 📦 Deployment

### Mobile App
```bash
cd mobile
expo build:ios
expo build:android
```

Or use EAS Build for modern builds:
```bash
eas build --platform all
```

### Web App (Vercel)
```bash
cd web
vercel deploy
```

Or connect your GitHub repository to Vercel for automatic deployments.

**Important**: Set the root directory to `web` in Vercel project settings.

## 🔐 Data Structure

### Item Data
```typescript
interface ItemData {
  qrCode: string;           // Unique QR code ID
  name: string;             // Item name
  ownerName: string;        // Owner's name
  ownerEmail: string;       // Owner's email
  status: 'active' | 'droppedOff';
  location?: Location;      // Drop-off location
  droppedOffAt?: string;    // Timestamp
  expiresAt?: string;       // 7-day deadline
}
```

### Drop-off Location
```typescript
interface Location {
  id: number;
  name: string;             // "Central Library"
  address: string;          // Full address
  phone: string;            // Contact number
}
```

## 🗺️ User Flows

### Register Item Flow
1. User opens mobile app
2. Taps "Register Item"
3. Enters item details (name, description)
4. QR code is generated and linked to item
5. User prints/sticks QR code on item

### Found Item Flow
1. Finder scans QR code with phone camera
2. Browser opens web app (`/found?qr=CODE`)
3. Finder sees item details and owner name (privacy protected)
4. Finder selects a drop-off location
5. Finder confirms drop-off
6. Owner receives notification
7. 7-day countdown begins
8. Owner picks up item

## 📱 QR Code Format

QR codes contain a URL linking to the web app:
```
https://qr-lost-found.vercel.app/found?qr=QR-1234567890
```

## 🔮 Future Enhancements

- [ ] Backend API with database (PostgreSQL/Firebase)
- [ ] Email notifications
- [ ] SMS notifications
- [ ] Admin dashboard for drop-off locations
- [ ] Premium subscription features
- [ ] Multiple language support
- [ ] Analytics and reporting
- [ ] Reward system for finders
- [ ] Integration with local lost & found services
- [ ] Blockchain-based ownership verification

## 🧪 Development

### Running Both Apps Simultaneously

Terminal 1 (Mobile):
```bash
cd mobile && npm start
```

Terminal 2 (Web):
```bash
cd web && npm run dev
```

### Testing the Integration

1. Register an item in the mobile app
2. Note the QR code ID
3. Open web browser to `http://localhost:3000/found?qr=YOUR_QR_CODE`
4. Test the found item flow

## 📝 Environment Variables

### Mobile App
Create `.env` in `mobile/`:
```env
EXPO_PUBLIC_API_URL=http://localhost:3000/api
```

### Web App
Create `.env.local` in `web/`:
```env
NEXT_PUBLIC_API_URL=http://localhost:3000/api
DATABASE_URL=your_database_url
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Feat(feature): add amazing feature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

MIT License - feel free to use this project for any purpose.

## 🆘 Support

For questions or issues:
- Create an issue in the repository
- Check the README files in `/mobile` and `/web` directories
- Review the code documentation

## 👥 Authors

Built with ❤️ to help reunite people with their belongings.

## 🙏 Acknowledgments

- Expo team for the amazing React Native framework
- Next.js team for the powerful web framework
- All contributors who help improve this project

---

**Made with 📱 by the QR Lost & Found Team**