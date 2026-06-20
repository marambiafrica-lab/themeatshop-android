# The Meat Stop - Android Application

A modern, feature-rich Android application for **The Meat Stop**, a premium meat retail outlet delivering fresh, quality meat products to households, restaurants, and businesses across Zimbabwe and the UK.

## 🎯 Overview

The Meat Stop app provides a seamless shopping experience with:
- **Home Screen**: Featured products and brand information
- **Shop Screen**: Browse products by category with search functionality
- **Cart Management**: Organize orders with customer details
- **WhatsApp Integration**: Direct ordering via WhatsApp
- **Contact Hub**: Multiple contact channels (WhatsApp, Email)
- **Material 3 Design**: Modern UI with orange/black brand theme

---

## 📋 Features

### Home Screen
- Brand introduction and tagline
- Featured product categories
- Key selling points (freshness, quality, pricing)
- Quick access to shop

### Shop Screen
- Product catalog with 10+ categories:
  - Fresh Beef
  - Pork Products
  - Chicken
  - Sausages
  - Mince Meat
  - Offals
  - Braai Packs
  - Bulk Orders
  - Custom Cutting
- Real-time search functionality
- Category filtering
- Price display
- Quick "Add to Cart" buttons

### Cart Screen
- Order summary with item count
- Customer information collection
  - Full name
  - Phone number
  - Delivery address
  - Special instructions
- WhatsApp ordering integration
- Cart management (clear cart option)

### Profile Screen
- Brand mission and values
- Contact information hub
- One-tap WhatsApp communication
- Benefits highlight
- Brand tagline and messaging

---

## 🎨 Design System

### Color Palette
- **Primary Orange**: `#FF8C00` (brand accent)
- **Dark Background**: `#1a1a1a` (main background)
- **Card Background**: `#2a2a2a` (secondary background)
- **Gold Accent**: `#D4A574` (premium touch)
- **Light Background**: `#FAFAFA` (light mode)

### Typography
- **Display**: Bold, large headings (28-32sp)
- **Headlines**: SemiBold (16-24sp)
- **Body**: Regular (14-16sp)
- **Labels**: Medium weight (12-14sp)

### Components
- Material 3 buttons with rounded corners
- Card-based layouts
- Bottom navigation bar
- Filter chips for category selection
- TextField inputs with orange focus states

---

## 🛠️ Technical Stack

### Language & Framework
- **Language**: Kotlin
- **UI Framework**: Jetpack Compose
- **Architecture**: MVVM-ready structure
- **Minimum SDK**: Android 7.0 (API 24)
- **Target SDK**: Android 14 (API 34)

### Key Dependencies
```gradle
// Compose
androidx.activity:activity-compose:1.8.1
androidx.compose.ui:ui:1.6.0
androidx.compose.material3:material3:1.1.2
androidx.compose.foundation:foundation:1.6.0

// Core
androidx.core:core-ktx:1.12.0
androidx.lifecycle:lifecycle-runtime-ktx:2.6.2
androidx.lifecycle:lifecycle-viewmodel-compose:2.6.2

// Navigation (for future expansion)
androidx.navigation:navigation-compose:2.7.5
```

---

## 📁 Project Structure

```
com/themeatstop/app/
├── MainActivity.kt                 # Entry point with navigation
├── ui/
│   ├── screens/
│   │   ├── HomeScreen.kt          # Home/landing screen
│   │   ├── ShopScreen.kt          # Product catalog with filtering
│   │   ├── CartScreen.kt          # Shopping cart & checkout
│   │   └── ProfileScreen.kt       # Account & contact info
│   └── theme/
│       ├── Theme.kt               # Material 3 theme configuration
│       └── Typography.kt          # Type scale definition
```

---

## 🚀 Getting Started

### Prerequisites
- Android Studio (Flamingo or newer)
- JDK 11 or higher
- Android SDK 34+
- Kotlin plugin enabled

### Setup Steps

1. **Clone the project**
   ```bash
   git clone <repository-url>
   cd themeatstop-android
   ```

2. **Open in Android Studio**
   - File → Open → Select project directory
   - Wait for Gradle sync to complete

3. **Build the project**
   ```bash
   ./gradlew build
   ```

4. **Run the app**
   - Connect an Android device or start an emulator
   - Click "Run" or press Shift+F10

---

## 📱 App Navigation

### Bottom Navigation
- **Home**: Dashboard with featured products
- **Shop**: Product catalog
- **Cart**: Shopping cart (badge shows item count)
- **Profile**: Account and contact information

### Navigation Flow
```
Home → Shop (Browse products)
        ↓
      Cart (Add items)
        ↓
      Profile (Account/Contact)
```

---

## 🔗 Integration Points

### WhatsApp Integration
- **UK Line**: +44 7428 913116
- **Zimbabwe Line**: [Configurable in code]
- **Deep Linking**: Uses WhatsApp API for direct ordering
- **Message Format**: Formatted with customer details and order summary

### Email
- **Contact Email**: orders@themeatstop.zw
- **Intent-based sharing** available

---

## 📊 Sample Product Data

The app comes pre-loaded with 12+ sample products:

| Product | Category | Price |
|---------|----------|-------|
| Beef Ribeye Steak | Fresh Beef | ZWL 2,450 |
| Pork Chops Pack | Pork | ZWL 1,200 |
| Chicken Breasts | Chicken | ZWL 950 |
| Premium Sausages | Sausages | ZWL 1,100 |
| Braai Pack Deluxe | Braai Packs | ZWL 3,500 |
| Custom Cut Service | Custom Cutting | Quote-based |

---

## 🔄 Future Enhancements

### Planned Features
- [ ] User authentication & accounts
- [ ] Order history tracking
- [ ] Payment integration (Stripe, PayPal)
- [ ] Push notifications
- [ ] Product images from API
- [ ] Real-time inventory updates
- [ ] Delivery tracking
- [ ] Customer reviews/ratings
- [ ] Wishlist functionality
- [ ] Multiple language support (Shona, Ndebele)

### Architecture Improvements
- [ ] ViewModel implementation for state management
- [ ] Repository pattern for data access
- [ ] Retrofit API client setup
- [ ] Local Room database for caching
- [ ] Coroutines for async operations

---

## 🧪 Testing

### Unit Tests
```bash
./gradlew test
```

### Instrumented Tests
```bash
./gradlew connectedAndroidTest
```

---

## 📝 Configuration

### Change Brand Colors
Edit `Theme.kt`:
```kotlin
val MeatStopOrange = Color(0xFFFF8C00)
val MeatStopDarkBg = Color(0xFF1a1a1a)
```

### Update Contact Information
Modify in `ProfileScreen.kt` and `CartScreen.kt`:
```kotlin
val whatsappPhone = "+44 7428 913116"
val emailAddress = "orders@themeatstop.zw"
```

### Add Products
Update the product list in `ShopScreen.kt`:
```kotlin
val products = listOf(
    Product(id, name, category, price, description, image)
)
```

---

## 🐛 Troubleshooting

### Build Issues
- Clear cache: `./gradlew clean`
- Rebuild: `./gradlew build`
- Check SDK versions in `build.gradle`

### Runtime Issues
- Ensure `compileSdk` matches installed SDK
- Check minimum SDK is API 24+
- Verify Compose version compatibility

### WhatsApp Integration
- Ensure device has WhatsApp installed
- Check phone number format (country code + number)
- Verify internet connectivity

---

## 📄 Strings Resource

Create `res/values/strings.xml`:
```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="app_name">The Meat Stop</string>
    <string name="tagline">Fresh Everyday!</string>
    <string name="slogan">From Farm to Table – Fresh, Quality Meat You Can Trust</string>
</resources>
```

---

## 🔐 Permissions

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

Optional future permissions:
- `android.permission.CAMERA` (for product photos)
- `android.permission.READ_CONTACTS` (for auto-fill)

---

## 📞 Support

**Contact The Meat Stop**
- WhatsApp (UK): +44 7428 913116
- Email: orders@themeatstop.zw
- Website: [To be configured]

---

## 📄 License

This project is proprietary to The Meat Stop. All rights reserved.

---

## ✅ Checklist for Deployment

- [ ] Update version code in `build.gradle`
- [ ] Update version name (semantic versioning)
- [ ] Test on multiple device sizes (phone & tablet)
- [ ] Test dark mode & light mode
- [ ] Verify WhatsApp integration
- [ ] Check all navigation flows
- [ ] Generate signed APK/AAB
- [ ] Upload to Google Play Store
- [ ] Create Play Store listing with screenshots

---

## 🤝 Contributing

For improvements or bug reports, contact the development team.

---

**Last Updated**: June 2026
**Version**: 1.0.0
**Status**: Production Ready
