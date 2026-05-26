You are a senior mobile app architect and authentication system engineer.
Analyze my existing game app codebase and implement a complete production-ready authentication and onboarding flow with proper session management, persistence, guest mode handling, and navigation architecture.

AUTH FLOW REQUIREMENTS

1. NEW USER FLOW
   For a completely new user, the app flow should be:

App Launch
→ Splash/App Loading
→ Sign In Page

* Sign Up with Google button
* Login button
* Play as Guest button
  → Username Setup Page
  → Terms & Conditions Page with checkbox confirmation
  → Levels Page
  → Game

Requirements:

* User cannot proceed without accepting Terms & Conditions.
* Username must be validated:

  * no empty username
  * prevent invalid characters if necessary
  * trim unnecessary spaces
* Persist onboarding completion state properly.

2. EXISTING GOOGLE USER FLOW
   If user has already signed up using Google and session/token exists:

App Launch
→ Splash/App Loading
→ Auto-login
→ Levels Page
→ Game

Requirements:

* No onboarding screens should appear again.
* Session restoration should be fast and reliable.
* Implement proper token/session validation.
* Handle expired session gracefully.

3. REINSTALL / RETURNING USER FLOW
   If user uninstalls and reinstalls the app:

App Launch
→ Splash/App Loading
→ Sign In Page

Then user should be able to:

* login using previously connected Google account
  OR
* login using previously created username/account system if applicable.

Requirements:

* Restore previous profile data after login.
* Restore:

  * levels
  * score
  * coins
  * progression
  * settings
* Prevent duplicate account creation.

4. GUEST USER FLOW
   If user clicks “Play as Guest”:

App Launch
→ Play as Guest
→ Username Setup
→ Terms & Conditions
→ Levels Page

Requirements:

* Guest username should persist locally.
* When guest reopens app:

  * continue with same guest username automatically
  * do NOT ask username repeatedly
* Maintain guest progression locally.
* Properly separate guest accounts from authenticated accounts.

5. LEVEL PAGE UI CHANGES
   Inside Levels Page:

* Place Settings button at top-right corner.
* Position it beside the coin display/update area.

Requirements:

* Remove Settings button completely from Game Page.
* Centralize app settings access only through Levels Page.
* Ensure clean responsive UI layout.

6. SETTINGS PAGE IMPROVEMENTS
   Inside Settings page:

* Add Logout button at the bottom/end.

Logout requirements:

* Clear active session properly.
* Navigate back to Sign In page.
* Preserve data correctly depending on account type.
* Prevent navigation bugs after logout.
* Handle:

  * Google logout
  * guest logout
  * local session cleanup

ARCHITECTURE REQUIREMENTS

Implement this in a scalable, production-ready architecture.

Requirements:

* Clean navigation flow
* Proper auth state management
* Persistent storage handling
* Session restoration
* Secure token handling
* Avoid duplicated navigation logic
* Prevent race conditions during app launch
* Prevent onboarding loop bugs
* Ensure smooth transitions between screens

STATE MANAGEMENT REQUIREMENTS

Ensure all user states are handled correctly:

* first-time user
* logged-in Google user
* returning user
* guest user
* logged-out user
* expired session user

Persist and restore:

* username
* progress
* levels
* coins
* settings
* achievements if applicable

UI/UX REQUIREMENTS

* Smooth transitions
* No flickering during auth checks
* Loading states where necessary
* Proper error handling
* Responsive mobile UI
* Clean onboarding experience

TESTING REQUIREMENTS

After implementation thoroughly test:

* first install flow
* Google login flow
* guest login flow
* reinstall flow
* logout flow
* session persistence
* onboarding completion
* navigation edge cases
* app restart behavior
* corrupted local storage handling

Finally:

* provide clean updated code
* explain major architectural changes
* explain auth/session flow implementation
* mention all assumptions made
* ensure final implementation is production-ready and scalable.
