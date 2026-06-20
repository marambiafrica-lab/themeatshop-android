# The Meat Stop - Android Development Quick Start

## 📚 Complete Project Files

This complete Android application includes all necessary files to build and run The Meat Stop app. Here's what you need to know to get started.

---

## 🎯 What You've Got

### Core Files Included

1. **MainActivity.kt** - App entry point with bottom navigation
2. **HomeScreen.kt** - Landing page with brand info
3. **ShopScreen.kt** - Product catalog with filtering
4. **CartScreen.kt** - Shopping cart with WhatsApp integration
5. **ProfileScreen.kt** - Account and contact hub
6. **Theme.kt** - Material 3 color scheme
7. **Typography.kt** - Type scale configuration
8. **AndroidManifest.xml** - App configuration
9. **build.gradle** - Dependencies and build config

---

## 🚀 Quick Start in 5 Minutes

### Step 1: Create Project Structure
```
app/src/main/
├── kotlin/com/themeatstop/app/
│   ├── MainActivity.kt
│   ├── ui/
│   │   ├── screens/
│   │   │   ├── HomeScreen.kt
│   │   │   ├── ShopScreen.kt
│   │   │   ├── CartScreen.kt
│   │   │   └── ProfileScreen.kt
│   │   └── theme/
│   │       ├── Theme.kt
│   │       └── Typography.kt
└── AndroidManifest.xml
```

### Step 2: Copy Files
1. Copy all `.kt` files to the `kotlin/com/themeatstop/app/` directory
2. Copy `AndroidManifest.xml` to `src/main/`
3. Copy `build.gradle` content to your app-level `build.gradle`

### Step 3: Sync & Build
```bash
./gradlew sync
./gradlew build
```

### Step 4: Run
- Connect device or start emulator
- Click "Run" button
- App launches!

---

## 🏗️ Architecture Overview

### Screen Composables
Each screen is a standalone composable function:

```kotlin
@Composable
fun HomeScreen(onNavigateToShop: () -> Unit)
```

**Key Pattern**:
- Pure composable functions
- State managed in composing function
- Callbacks for navigation

### Navigation Model
```kotlin
sealed class Screen {
    object Home : Screen()
    object Shop : Screen()
    object Cart : Screen()
    object Profile : Screen()
}
```

Simple state-based navigation in MainActivity.

### Theme System
Material 3 with custom colors:
- `DarkColorScheme` for dark mode
- `LightColorScheme` for light mode
- Automatic theme switching based on system preference

---

## 📱 Screen Breakdown

### 1️⃣ HomeScreen
**File**: `HomeScreen.kt`
**Purpose**: Welcome & featured products
**Key Components**:
- Brand header
- Featured banner
- Feature list (checkmarks)
- Category quick links
- CTA button

```kotlin
// Custom composables used:
// - Card layouts
// - Row/Column for layout
// - Icon components with Verified icon
```

### 2️⃣ ShopScreen
**File**: `ShopScreen.kt`
**Purpose**: Product browsing & filtering
**Key Components**:
- Search bar with TextField
- Category filter chips (LazyRow)
- Product grid (LazyColumn)
- ProductCard composable

```kotlin
// Data structure
data class Product(
    val id: Int,
    val name: String,
    val category: String,
    val price: Double,
    val description: String,
    val image: String
)
```

**Features**:
- Real-time search filtering
- Category-based filtering
- Combined search + category filtering
- Product cards with add-to-cart

### 3️⃣ CartScreen
**File**: `CartScreen.kt`
**Purpose**: Order management & checkout
**Key Components**:
- Cart summary
- Customer form (4 fields)
- WhatsApp order button
- Clear cart button

**WhatsApp Integration**:
```kotlin
val whatsappUrl = "https://api.whatsapp.com/send?phone={number}&text={message}"
val intent = Intent(Intent.ACTION_VIEW).apply {
    data = Uri.parse(whatsappUrl)
}
context.startActivity(intent)
```

**Form Validation**:
- Button enabled only when all required fields filled
- Name, phone, address are required

### 4️⃣ ProfileScreen
**File**: `ProfileScreen.kt`
**Purpose**: Brand info & customer support
**Key Components**:
- Brand header with logo
- Mission statement
- Contact cards (WhatsApp, Email)
- Benefits list
- Core values grid

**Reusable Composables**:
```kotlin
@Composable
fun ContactCard(icon: ImageVector, title: String, subtitle: String)

@Composable
fun BenefitItem(icon: String, title: String, description: String)
```

---

## 🎨 Design System Usage

### Colors
```kotlin
// In Theme.kt
val MeatStopOrange = Color(0xFFFF8C00)
val MeatStopDarkBg = Color(0xFF1a1a1a)
val MeatStopDarkGrey = Color(0xFF2a2a2a)
```

### Usage Example
```kotlin
Button(
    colors = ButtonDefaults.buttonColors(
        containerColor = MeatStopOrange
    )
)
```

### Typography
```kotlin
// Defined in Typography.kt
Text(
    "Headline",
    style = MaterialTheme.typography.headlineLarge
)
```

---

## 🔄 State Management

### Current Approach (Simple State)
```kotlin
var currentScreen by remember { mutableStateOf<Screen>(Screen.Home) }
var cartItemCount by remember { mutableStateOf(0) }
var searchQuery by remember { mutableStateOf("") }
```

### Future: ViewModel Approach
```kotlin
class CartViewModel : ViewModel() {
    val cartItems = MutableLiveData<List<Product>>()
    
    fun addToCart(product: Product) {
        // Logic here
    }
}
```

---

## 🔧 Common Customizations

### Change Brand Color
```kotlin
// Theme.kt
val MeatStopOrange = Color(0xFFFF8C00)  // Change this
```

### Update WhatsApp Number
```kotlin
// CartScreen.kt & ProfileScreen.kt
val whatsappPhone = "+44 7428 913116"  // Change to Zimbabwe number
```

### Add More Products
```kotlin
// ShopScreen.kt - Update products list
val products = listOf(
    Product(
        id = 13,
        name = "New Product",
        category = "Fresh Beef",
        price = 1500.0,
        description = "Description",
        image = ""
    )
)
```

### Change App Name
```xml
<!-- strings.xml -->
<string name="app_name">The Meat Stop</string>
```

---

## 📦 Composable Patterns Used

### 1. State Hoisting
```kotlin
@Composable
fun ShopScreen(onAddToCart: () -> Unit) {
    var searchQuery by remember { mutableStateOf("") }
    // Pass state up, UI down
}
```

### 2. Component Composition
```kotlin
@Composable
fun ProductCard(product: Product) {
    Card { /* content */ }
}
```

### 3. Conditional UI
```kotlin
if (cartCount == 0) {
    Text("Empty cart")
} else {
    // Cart content
}
```

### 4. Lists & LazyLoading
```kotlin
LazyColumn { items(products) { product -> ... } }
```

### 5. Intent Integration
```kotlin
val context = LocalContext.current
Intent(Intent.ACTION_VIEW).apply {
    data = Uri.parse(whatsappUrl)
}.let { context.startActivity(it) }
```

---

## 🔌 External Integrations

### WhatsApp Deep Linking
```kotlin
val message = "Order details here"
val encodedMessage = Uri.encode(message)
val url = "https://api.whatsapp.com/send?phone={phoneNumber}&text=$encodedMessage"
```

**Requirements**:
- WhatsApp installed on device
- Valid phone number with country code
- Message encoded with Uri.encode()

### Email Intent
```kotlin
Intent(Intent.ACTION_SENDTO).apply {
    data = Uri.parse("mailto:email@example.com")
}.let { context.startActivity(it) }
```

---

## 🎯 How Navigation Works

### Current Implementation
```kotlin
var currentScreen by remember { mutableStateOf<Screen>(Screen.Home) }

Scaffold(
    bottomBar = {
        NavigationBar {
            NavigationBarItem(
                selected = currentScreen == Screen.Home,
                onClick = { currentScreen = Screen.Home }
            )
        }
    }
) {
    when (currentScreen) {
        Screen.Home -> HomeScreen()
        Screen.Shop -> ShopScreen()
        // ...
    }
}
```

### To Add New Screen
1. Add to `sealed class Screen`
2. Add `NavigationBarItem` for it
3. Add `when` branch in Scaffold content

---

## 📊 Cart Count Badge

The cart shows item count in top-right corner:
```kotlin
Badge(
    containerColor = Color(0xFFFF8C00),
    modifier = Modifier.offset(x = 12.dp, y = -8.dp)
) {
    Text(cartItemCount.toString())
}
```

Update with: `cartItemCount++`

---

## 🎬 Adding Animations (Future)

```kotlin
// Fade in text
val alpha by animateFloatAsState(
    targetValue = if (visible) 1f else 0f
)
Text("Hello", modifier = Modifier.alpha(alpha))
```

---

## 🧪 Testing Tips

### Manual Testing Checklist
- [ ] Navigation between all 4 screens works
- [ ] Search filters products correctly
- [ ] Category filter works
- [ ] Add to cart increments badge
- [ ] Cart form validation works
- [ ] WhatsApp button opens with correct message
- [ ] Looks good on phone & tablet
- [ ] Dark mode works
- [ ] Light mode works

### Device Sizes to Test
- Phone (Small: 4.7", Medium: 5.5", Large: 6.7")
- Tablet (7", 10")

---

## 🚀 Performance Optimization Tips

1. **LazyColumn** for lists (already implemented)
2. Use `remember` for expensive computations
3. Extract composables for reusability
4. Use `key` in lists for stability

---

## 📚 Learning Resources

- [Compose Basics](https://developer.android.com/develop/ui/compose)
- [Material Design 3](https://m3.material.io/)
- [Kotlin Docs](https://kotlinlang.org/docs/home.html)

---

## ❓ FAQ

**Q: How do I change the app name?**
A: Update `app_name` in `strings.xml`

**Q: How do I add more products?**
A: Add entries to `products` list in `ShopScreen.kt`

**Q: Can I use this app without WhatsApp?**
A: Currently requires WhatsApp. Can add email fallback.

**Q: How do I add payment integration?**
A: See Future Enhancements section in README

**Q: Can I use this for iOS?**
A: This is Android only. Would need Swift/SwiftUI for iOS.

---

## 🎓 Next Steps

1. **Build & Run** - Get it working on your device
2. **Customize Colors** - Match your branding
3. **Add Real Products** - Replace sample data
4. **Test Thoroughly** - Check all flows
5. **Deploy** - Publish to Google Play Store

---

**Happy Building! 🎉**

For questions or support, contact The Meat Stop team.

---

**Version**: 1.0.0 | **Updated**: June 2026
