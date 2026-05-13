Act as a senior mobile game architect, SaaS system designer, and Play Store compliance expert.

Build a production-ready, scalable Block Blast game app with full monetization and backend architecture.

TECH STACK:
- Flutter (latest stable)
- Clean Architecture
- State management: Riverpod or Bloc
- Backend: Firebase (Auth + Firestore + Cloud Functions)
- AdMob integration
- Secure production setup

-----------------------------------
1. UI REQUIREMENTS
-----------------------------------
- Recreate the exact UI from provided screens.
- Match layout precisely.
- Implement proper navigation flow.
- Use responsive design.
- Add smooth animations everywhere.
- Use modern clean UI.
- Add haptic feedback.

-----------------------------------
2. CORE GAME LOGIC
-----------------------------------
- Grid-based board system.
- Drag and drop blocks.
- Collision detection.
- Row and column clear logic.
- Score system.
- Level progression.
- Game over detection (no valid moves).
- Win condition system.
- Optimized performance.
- Modular reusable logic.

-----------------------------------
3. ANIMATIONS
-----------------------------------
- Button press animation.
- Block placement animation.
- Line clear blast animation with particle effects.
- Game over animation.
- Win celebration animation.
- Screen transition animations.

-----------------------------------
4. SOUND SYSTEM
-----------------------------------
- Click sound.
- Block drop sound.
- Blast sound.
- Win sound.
- Game over sound.
- Sound toggle in settings.
- Persistent user preference storage.

-----------------------------------
5. ADS INTEGRATION (AdMob)
-----------------------------------
- Banner ads (home screen).
- Interstitial ads (after game over).
- Rewarded ads (extra coins / revive).
- Ad frequency control.
- Remote config control for ads.
- Comply with Google Play policies.

-----------------------------------
6. IN-APP PURCHASES
-----------------------------------
- Remove ads purchase.
- Coin packs.
- Power-up bundles.
- Use Google Play Billing.
- Secure purchase validation.
- Server-side verification.

-----------------------------------
7. SUBSCRIPTION MODEL
-----------------------------------
- Monthly premium subscription.
- Benefits:
   - Remove ads.
   - Exclusive themes.
   - Bonus rewards.
   - Cloud save priority.
- Handle subscription status via backend verification.

-----------------------------------
8. DAILY REWARDS SYSTEM
-----------------------------------
- Daily login reward.
- Streak system.
- Increasing rewards.
- Server-validated to prevent cheating.
- Time-based validation.
- Store reward state in Firestore.

-----------------------------------
9. POWER-UPS SYSTEM
-----------------------------------
Add in-game boosters:
- Undo move.
- Shuffle blocks.
- Bomb clear.
- Extra slot.
- Revive after game over.
- Consumable coin-based system.

-----------------------------------
10. OFFLINE MODE
-----------------------------------
- Game playable without internet.
- Local storage for scores.
- Sync when online.
- Graceful fallback.

-----------------------------------
11. CLOUD SAVE
-----------------------------------
- User authentication (Google + Email).
- Save:
   - Score
   - Level
   - Coins
   - Settings
- Firestore integration.
- Real-time sync.

-----------------------------------
12. ANTI-CHEAT PROTECTION
-----------------------------------
- Server-side score validation.
- Prevent local score manipulation.
- Secure cloud functions.
- Validate purchases on server.
- Detect abnormal score jumps.
- Use Firebase security rules.
- Obfuscate code for release build.

-----------------------------------
13. ADMIN DASHBOARD
-----------------------------------
Create a simple web admin panel:
- View users.
- View revenue.
- Manage rewards.
- Control daily reward values.
- Enable/disable ads remotely.
- Send push notifications.
- Use Firebase or simple Node.js dashboard.

-----------------------------------
14. ANALYTICS
-----------------------------------
Integrate:
- Firebase Analytics.
- Track:
   - Game start.
   - Game over.
   - Level completion.
   - Ad impressions.
   - Purchases.
   - Retention.
- Track user behavior for optimization.

-----------------------------------
15. PLAY STORE READINESS
-----------------------------------
- Follow Google Play policies.
- Add privacy policy integration.
- Data safety section compliance.
- Secure API keys.
- No hardcoded secrets.
- Proper app signing.
- Release build optimization.
- Proguard enabled.
- Versioning system.

-----------------------------------
16. PROJECT STRUCTURE
-----------------------------------
Provide full folder structure:
- presentation/
- domain/
- data/
- services/
- models/
- widgets/
- core/
- utils/

Use clean architecture principles.

-----------------------------------
OUTPUT REQUIRED:
-----------------------------------
- Complete code implementation.
- Backend setup guide.
- Firebase configuration steps.
- AdMob setup steps.
- Play Store deployment checklist.
- Security best practices.
- Monetization flow diagram.
