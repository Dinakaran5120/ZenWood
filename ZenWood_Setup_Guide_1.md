# ZenWood: Classic Block Blast
## Complete Setup Guide — From Zero to Play Store

---

# PHASE 1 — Install Flutter & Tools

## Step 1.1 — Install Flutter SDK

**Windows:**
1. Download Flutter SDK from https://flutter.dev/docs/get-started/install/windows
2. Extract to `C:\flutter`
3. Add `C:\flutter\bin` to your **System PATH**
4. Open Command Prompt → run: `flutter doctor`

**Mac:**
```bash
brew install flutter
flutter doctor
```

**Linux:**
```bash
sudo snap install flutter --classic
flutter doctor
```

✅ **You should see:** `Flutter (Channel stable, 3.x.x)`

---

## Step 1.2 — Install Android Studio

1. Download from https://developer.android.com/studio
2. Install with default settings
3. Open Android Studio → SDK Manager → Install:
   - Android SDK Platform 34
   - Android SDK Build-Tools 34
   - Android Emulator
4. Run `flutter doctor` again → all Android items should show ✅

---

## Step 1.3 — Install VS Code (Recommended Editor)

1. Download from https://code.visualstudio.com
2. Install these extensions:
   - **Flutter** (by Dart Code)
   - **Dart** (by Dart Code)
   - **Firebase** (by toba)

---

## Step 1.4 — Install Node.js (for Firebase Functions)

1. Download from https://nodejs.org → choose LTS version
2. Verify: `node --version` → should show v18+
3. Install Firebase CLI:
```bash
npm install -g firebase-tools
firebase --version
```

---

# PHASE 2 — Set Up the Flutter Project

## Step 2.1 — Create Flutter Project

```bash
# Navigate to where you want your project
cd Documents

# Create new Flutter project
flutter create zenwood --org com.yourname --platforms android,ios

# This creates the base project structure
cd zenwood
```

> ⚠️ Replace `com.yourname` with your actual reverse domain (e.g. `com.karthikdev`)

---

## Step 2.2 — Copy ZenWood Source Files

1. Extract the downloaded `zenwood_flutter_v2.zip`
2. You'll see a `zenwood/` folder inside
3. Copy these folders/files INTO your Flutter project (overwrite existing):

```
zenwood_flutter_v2/zenwood/lib/          → your_project/lib/
zenwood_flutter_v2/zenwood/pubspec.yaml  → your_project/pubspec.yaml
zenwood_flutter_v2/zenwood/functions/    → your_project/functions/
zenwood_flutter_v2/zenwood/firestore.rules → your_project/firestore.rules
zenwood_flutter_v2/zenwood/LAUNCH_GUIDE.md → your_project/
zenwood_flutter_v2/zenwood/android/app/src/main/AndroidManifest.xml
  → your_project/android/app/src/main/AndroidManifest.xml
```

---

## Step 2.3 — Install Dependencies

```bash
flutter pub get
```

✅ Should complete without errors.

---

## Step 2.4 — Add Assets

Create these folders inside your project and add files:

```
assets/
├── images/
│   ├── wood_bg.png          ← Dark wood texture (download free from freepik.com)
│   ├── wood_panel.png       ← Medium wood texture
│   ├── wood_btn.png         ← Light wood texture
│   ├── wood_block.png       ← Block wood texture
│   ├── logo_blocks.png      ← Your app logo blocks image
│   ├── leaf_cluster.png     ← Green leaves decoration
│   ├── coin.png             ← Gold coin icon
│   └── default_avatar.png   ← Default user avatar
├── sounds/
│   ├── click.mp3
│   ├── block_drop.mp3
│   ├── blast.mp3
│   ├── combo.mp3
│   ├── game_over.mp3
│   ├── win.mp3
│   ├── new_best.mp3
│   ├── reward.mp3
│   └── bg_music.mp3
└── fonts/
    ├── LilitaOne-Regular.ttf    ← Download from Google Fonts
    ├── Nunito-Regular.ttf       ← Download from Google Fonts
    ├── Nunito-Bold.ttf
    └── Nunito-ExtraBold.ttf
```

**Free resource links:**
- Wood textures: https://www.freepik.com/search?query=wood+texture+seamless (free license)
- Fonts: https://fonts.google.com/specimen/Lilita+One and https://fonts.google.com/specimen/Nunito
- Sounds: https://mixkit.co/free-sound-effects/game/ (free license)
- Coin icon: https://www.flaticon.com/search?word=gold+coin (free license)

---

# PHASE 3 — Firebase Setup

## Step 3.1 — Create Firebase Project

1. Go to https://console.firebase.google.com
2. Click **"Add project"**
3. Project name: `ZenWood`
4. Enable Google Analytics: **Yes**
5. Analytics account: Default Account for Firebase
6. Click **"Create project"** → wait ~30 seconds

---

## Step 3.2 — Add Android App to Firebase

1. In Firebase Console → click the **Android icon** (Add app)
2. Fill in:
   - **Android package name:** `com.yourname.zenwood` ← MUST match your flutter create command
   - **App nickname:** ZenWood
   - **Debug signing certificate SHA-1:** (skip for now, add later)
3. Click **"Register app"**
4. Download **`google-services.json`**
5. Place it here: `android/app/google-services.json`
6. Click Next → Next → Continue to Console

---

## Step 3.3 — Configure Android Gradle Files

Open `android/build.gradle` and add inside `dependencies {}`:
```groovy
classpath 'com.google.gms:google-services:4.4.0'
```

Open `android/app/build.gradle` and add at the very **bottom**:
```groovy
apply plugin: 'com.google.gms.google-services'
```

Also set these in the same file under `android { defaultConfig { ... } }`:
```groovy
minSdkVersion 21
targetSdkVersion 34
```

---

## Step 3.4 — Enable Firebase Services

In Firebase Console, enable each service:

**Authentication:**
1. Build → Authentication → Get started
2. Sign-in method → Enable **Email/Password**
3. Sign-in method → Enable **Google**
   - Add your Support email
   - Save

**Firestore Database:**
1. Build → Firestore Database → Create database
2. Select **"Start in production mode"**
3. Choose server location closest to India: `asia-south1 (Mumbai)`
4. Done

**Cloud Functions:**
1. Build → Functions → Get started
2. You'll need to **upgrade to Blaze (pay-as-you-go)** plan
   - Go to Project Settings → Usage and billing → Modify plan → Blaze
   - Free tier is generous: first 2M function calls/month are free

**Remote Config:**
1. Engage → Remote Config → Create configuration
2. Add these parameters:

| Parameter Key | Default Value | Type |
|--------------|--------------|------|
| `ads_enabled` | `true` | Boolean |
| `interstitial_frequency` | `3` | Number |
| `daily_reward_multiplier` | `1` | Number |
| `show_rewarded_ads` | `true` | Boolean |

3. Click **Publish changes**

---

## Step 3.5 — FlutterFire CLI (Auto-generates config)

```bash
# Install FlutterFire CLI
dart pub global activate flutterfire_cli

# Configure (run inside your project folder)
flutterfire configure --project=YOUR-FIREBASE-PROJECT-ID
```

> Find your project ID in Firebase Console → Project Settings → General → Project ID

This automatically generates `lib/firebase_options.dart` — **do not edit this file manually.**

---

## Step 3.6 — Deploy Firestore Security Rules

```bash
# Login to Firebase
firebase login

# Initialize Firebase in your project (run inside project folder)
firebase init

# Select with spacebar:
# ✅ Firestore
# ✅ Functions
# Then press Enter

# Use existing project → select ZenWood
# Accept default file names

# Deploy rules
firebase deploy --only firestore:rules
```

---

## Step 3.7 — Deploy Cloud Functions

```bash
cd functions
npm install
cd ..
firebase deploy --only functions
```

✅ You should see: `✔ Deploy complete!` with 4 function URLs

---

# PHASE 4 — AdMob Setup

## Step 4.1 — Create AdMob Account

1. Go to https://admob.google.com
2. Sign in with your Google account
3. Fill in account details → Country: India → Currency: INR
4. Accept terms → **Create AdMob account**

---

## Step 4.2 — Add Your App

1. Apps → **Add app**
2. Platform: **Android**
3. Is the app listed on a supported app store? → **No** (until you publish)
4. App name: `ZenWood: Classic Block Blast`
5. Copy your **AdMob App ID** → looks like: `ca-app-pub-1234567890123456~1234567890`

---

## Step 4.3 — Create 3 Ad Units

**Banner Ad:**
1. Your app → Add ad unit → **Banner**
2. Ad unit name: `zenwood_home_banner`
3. Copy the **Ad unit ID**

**Interstitial Ad:**
1. Add ad unit → **Interstitial**
2. Ad unit name: `zenwood_gameover_inter`
3. Copy the **Ad unit ID**

**Rewarded Ad:**
1. Add ad unit → **Rewarded**
2. Ad unit name: `zenwood_rewarded`
3. Reward amount: `50`, Reward item: `coins`
4. Copy the **Ad unit ID**

---

## Step 4.4 — Replace Test IDs with Real IDs

Open `lib/core/constants/app_constants.dart` and replace:

```dart
// Replace these 4 values:
static const String admobAppIdAndroid = 'YOUR_ADMOB_APP_ID';
static const String bannerAdUnitAndroid = 'YOUR_BANNER_AD_UNIT_ID';
static const String interstitialAdUnitAndroid = 'YOUR_INTERSTITIAL_AD_UNIT_ID';
static const String rewardedAdUnitAndroid = 'YOUR_REWARDED_AD_UNIT_ID';
```

Also open `android/app/src/main/AndroidManifest.xml` and replace:
```xml
android:value="YOUR_ADMOB_APP_ID"
```

> ⚠️ Use **test IDs during development**, replace with real IDs only before final release build.

---

# PHASE 5 — Google Play In-App Purchases Setup

## Step 5.1 — Create Play Console Account

1. Go to https://play.google.com/console
2. Sign in with Google account
3. Pay **one-time $25 USD** registration fee
4. Complete identity verification (takes 1-2 days)

---

## Step 5.2 — Create the App in Play Console

1. All apps → **Create app**
2. App name: `ZenWood: Classic Block Blast`
3. Default language: English
4. App or game: **Game**
5. Free or paid: **Free**
6. Accept policies → Create app

---

## Step 5.3 — Create In-App Products

Go to your app → Monetize → **In-app products** → Create product:

| Product ID | Name | Price (INR) | Type |
|-----------|------|------------|------|
| `zenwood_remove_ads` | Remove Ads | ₹199 | One-time |
| `zenwood_coins_100` | 100 Coins | ₹49 | One-time |
| `zenwood_coins_500` | 500 Coins | ₹179 | One-time |
| `zenwood_coins_1200` | 1200 Coins | ₹349 | One-time |
| `zenwood_power_bundle` | Power Bundle | ₹249 | One-time |

Go to **Subscriptions** → Create subscription:

| Product ID | Name | Price | Period |
|-----------|------|-------|--------|
| `zenwood_premium_monthly` | ZenWood Premium | ₹99/month | Monthly |

---

# PHASE 6 — Build & Sign the App

## Step 6.1 — Generate Release Keystore

Run this command **once** and store the file safely:

```bash
keytool -genkey -v \
  -keystore ~/zenwood-release.keystore \
  -alias zenwood \
  -keyalg RSA \
  -keysize 2048 \
  -validity 10000
```

Fill in when prompted:
- Keystore password: (choose strong password)
- First and last name: Your Name
- Organization: Your company name
- City, State, Country: Your details

> 🔴 **CRITICAL: Back up this .keystore file to Google Drive/external drive. If you lose it, you can NEVER update your app on Play Store.**

---

## Step 6.2 — Configure App Signing

Create file `android/key.properties`:
```properties
storePassword=YOUR_KEYSTORE_PASSWORD
keyPassword=YOUR_KEY_PASSWORD
keyAlias=zenwood
storeFile=C:/Users/YourName/zenwood-release.keystore
```
(On Mac/Linux: `/Users/YourName/zenwood-release.keystore`)

Open `android/app/build.gradle` and add **before** the `android {` block:
```groovy
def keystoreProperties = new Properties()
def keystorePropertiesFile = rootProject.file('key.properties')
if (keystorePropertiesFile.exists()) {
    keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
}
```

Inside `android { ... }`, add signing config:
```groovy
signingConfigs {
    release {
        keyAlias keystoreProperties['keyAlias']
        keyPassword keystoreProperties['keyPassword']
        storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
        storePassword keystoreProperties['storePassword']
    }
}
buildTypes {
    release {
        signingConfig signingConfigs.release
        minifyEnabled true
        shrinkResources true
        proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
    }
}
```

---

## Step 6.3 — Add ProGuard Rules

Create/open `android/app/proguard-rules.pro` and add:
```
-keep class io.flutter.** { *; }
-keep class io.flutter.plugins.** { *; }
-keep class com.google.firebase.** { *; }
-keep class com.google.android.gms.** { *; }
-keep public class com.google.android.gms.ads.** { public *; }
-keep class com.android.vending.billing.** { *; }
```

---

## Step 6.4 — Add .gitignore Entries

Open `.gitignore` and add:
```
# Secrets - NEVER commit these
android/key.properties
android/app/google-services.json
ios/Runner/GoogleService-Info.plist
lib/firebase_options.dart
*.keystore
*.jks
```

---

## Step 6.5 — Build Release App Bundle

```bash
flutter clean
flutter pub get
flutter build appbundle --release
```

✅ Output file: `build/app/outputs/bundle/release/app-release.aab`

This `.aab` file is what you upload to Play Store.

---

# PHASE 7 — Play Store Submission

## Step 7.1 — Complete Store Listing

In Play Console → your app → **Store listing**:

**Short description** (80 chars max):
```
Place wooden blocks, clear lines & blast your way to the top score!
```

**Full description:**
```
ZenWood is the ultimate classic block blast puzzle game with a beautiful wooden theme. Relax your mind while strategically placing blocks to clear lines and earn massive scores.

🌿 FEATURES
• Classic 8×8 grid gameplay
• Beautiful wooden theme with smooth animations  
• Global leaderboard – compete with players worldwide
• Daily rewards & streak bonuses
• Power-ups: Undo, Shuffle, Bomb, Extra Slot, Revive
• Cloud save – your progress syncs everywhere
• Play offline anytime

🏆 HOW TO PLAY
• Drag and drop blocks onto the board
• Fill complete rows or columns to blast them away
• Chain multiple clears for combo bonuses
• Game ends when no blocks can be placed

🎮 PREMIUM FEATURES
• Remove all ads for uninterrupted play
• Monthly subscription with exclusive themes
• Bonus coin rewards for subscribers
```

---

## Step 7.2 — Upload Graphics

| Asset | Size | Tool to Create |
|-------|------|---------------|
| App icon | 512×512 PNG | Figma / Canva |
| Feature graphic | 1024×500 PNG | Figma / Canva |
| Screenshots (min 2) | 1080×1920 px | Android Emulator screenshot |

**Take screenshots:**
1. Run app on emulator or phone
2. Navigate to each screen
3. Press Volume Down + Power (phone) or use emulator screenshot button

---

## Step 7.3 — Content Rating

1. Play Console → Policy → **App content**
2. Content rating → Start questionnaire
3. Category: **Games**
4. Answer all questions honestly (no violence, no mature content = Everyone rating)
5. Submit → Rating applied automatically

---

## Step 7.4 — Data Safety

1. Play Console → Policy → **Data safety**
2. Fill in the form:

| Data type | Collected | Shared | Optional |
|-----------|-----------|--------|----------|
| Name | ✅ | ❌ | ✅ |
| Email address | ✅ | ❌ | ✅ |
| User IDs | ✅ | ❌ | ❌ |
| Purchase history | ✅ | ❌ | ❌ |
| App interactions | ✅ | ✅ (Analytics) | ❌ |
| Crash logs | ✅ | ✅ (Firebase) | ❌ |

3. Data is encrypted in transit: **Yes**
4. Users can request deletion: **Yes**

---

## Step 7.5 — Privacy Policy

You MUST have a public privacy policy URL. Quickest way:

1. Go to https://app.privacypolicies.com/wizard/privacy-policy (free)
2. Fill in your app name and details
3. Generate policy
4. Host it on GitHub Pages or your website
5. Paste the URL in Play Console → Store listing → Privacy policy URL

---

## Step 7.6 — Upload AAB & Release

1. Play Console → Testing → **Internal testing** → Create new release
2. Upload your `app-release.aab`
3. Add release notes: `Initial release`
4. Save → Review release → Start rollout

**Add testers** (need 3+ for Internal testing):
1. Internal testing → Testers → Manage list
2. Add email addresses
3. Share the opt-in URL with them
4. Have them install and test on real Android device

**After testing passes → promote to Production:**
1. Internal testing → Promote release → Production
2. Set rollout percentage: start with 20%
3. Review → Rollout to production

⏳ Google review takes **3–7 business days** for first submission.

---

# PHASE 8 — Post-Launch

## Monitor Your App

**Firebase Console:**
- Analytics → Real-time users
- Crashlytics (add to pubspec.yaml) → crash reports
- Performance → screen load times

**Play Console:**
- Android vitals → crash rate, ANR rate
- Reviews → reply to users
- Statistics → installs, ratings, revenue

## Update the App

When you fix bugs or add features:
1. Increment version in `pubspec.yaml`:
   ```yaml
   version: 1.0.1+2  # format: display_version+build_number
   ```
2. Build new AAB: `flutter build appbundle --release`
3. Upload to Play Console → Create new release

---

# QUICK REFERENCE — Common Commands

```bash
# Run app in debug mode
flutter run

# Run on specific device
flutter run -d emulator-5554

# List connected devices
flutter devices

# Clean build cache
flutter clean

# Get packages
flutter pub get

# Build release AAB
flutter build appbundle --release

# Build release APK (for direct install testing)
flutter build apk --release

# Check for issues
flutter analyze

# Deploy Firebase functions
firebase deploy --only functions

# Deploy Firestore rules
firebase deploy --only firestore:rules
```

---

# TROUBLESHOOTING

| Error | Fix |
|-------|-----|
| `google-services.json not found` | Place file at `android/app/google-services.json` |
| `flutter pub get` fails | Check `pubspec.yaml` indentation (use spaces not tabs) |
| AdMob ads not showing | Check App ID in `AndroidManifest.xml` matches AdMob console |
| Firebase Auth fails | Enable sign-in methods in Firebase Console |
| Build fails with Kotlin error | Update Kotlin version in `android/build.gradle` to `1.8.0` |
| `firebase_options.dart not found` | Run `flutterfire configure` again |
| Keystore error | Check path in `key.properties` uses forward slashes `/` |
| Play Store rejects AAB | Ensure `minSdkVersion 21`, `targetSdkVersion 34` |
| In-App Purchase not working | Add tester email in Play Console → License Testing |

---

**Estimated Total Setup Time: 4–6 hours for a developer familiar with mobile development.**

For support and questions, refer to:
- Flutter docs: https://flutter.dev/docs
- Firebase docs: https://firebase.google.com/docs
- AdMob docs: https://developers.google.com/admob
- Play Console help: https://support.google.com/googleplay/android-developer
