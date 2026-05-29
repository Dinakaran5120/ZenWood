You are working on an existing Flutter + Flame block puzzle game project. Fix the following issues carefully WITHOUT breaking existing game logic, Firebase auth flow, gameplay, animations, rewards, levels, or UI responsiveness.

Important:

* Maintain smooth gameplay performance.
* Do not modify unrelated systems.
* Test all fixes after implementation.
* Preserve existing pages/screens and reuse them instead of creating duplicates.

---

1. Store Page Navigation Fix

---

Inside the Store page:

* When the user clicks "Spin Wheel", open the already existing Spin Wheel page.
* When the user clicks "Daily Rewards", open the already existing Daily Rewards page.
* Ensure all store buttons correctly redirect to their corresponding existing screens.

---

2. Critical Block Shape Mutation Bug

---

Current issue:

* When dragging a block to the board, the block changes into another shape unexpectedly.
  Example:
* User selects an L-shaped block.
* While placing it on the board, it changes into a square block.

Fix:

* Ensure the selected block retains the exact same shape during drag and placement.
* Prevent state mutation, reference overwrites, rerender replacement, index mismatch, or cloning issues.
* The dragged block instance and rendered preview must remain identical.

This is a HIGH PRIORITY gameplay bug.

---

3. Email Login Recovery Fix

---

Current issue:

* Existing users cannot log in using their original email.
* System says "Account not found".

Fix:

* During login, check Firebase Authentication properly using email.
* If the email exists, allow account recovery/login correctly.
* Ensure previously created accounts remain accessible.

---

4. Remove Username Requirement During Login

---

Current behavior:

* Login requires both username and email.

Fix:

* Users should log in ONLY using email + password.
* Username should only be used during account creation/profile setup.
* Remove username field completely from login flow/UI.

---

5. Free Coins Reward Ad Flow

---

When user clicks:

* Coins
* Free Coins

Then:

* Show a "Watch Ad" button.
* After watching rewarded ad successfully, grant 50 coins.
* Ensure reward cannot be exploited repeatedly without ad completion.
* Update coin balance instantly in UI and Firebase if applicable.

---

6. Settings Button Relocation

---

Fix UI placement:

* Remove Settings button from Levels page.
* Add Settings button to the Game Board page at the top-right corner.
* Ensure navigation/settings functionality still works correctly.

---

7. Player Rank Display

---

On the Levels page:

* At the top-right corner beside the coins/upgrades section,
  show the player rank.
  Examples:
* Bronze
* Silver
* Gold
* Diamond

Use existing player progression/rank system if already available.

---

8. Game Sound Effects & Audio Improvements

---

Add proper sound effects for:

* Game start
* Block placement
* Line clear/blast
* Reward received
* Gift collection
* Purchase success
* Win/victory

Ensure:

* Sounds are not overlapping excessively.
* Audio volume is balanced.
* Flame Audio lifecycle is handled properly.

---

9. Old App Icon Still Appearing

---

Issue:

* App icon was changed but old icon still appears during app loading/splash/startup.

Fix:

* Remove all cached old launcher icons and splash assets.
* Regenerate launcher icons properly.
* Ensure Zenblast/Zenblock branding appears everywhere:

  * launcher icon
  * splash screen
  * app loading screen
  * recent apps screen

Perform:

* flutter clean
* regenerate icons
* rebuild assets

---

10. Background Music Continues After Exiting App

---

Current issue:

* Music continues playing even after user exits/minimizes the app.

Fix:

* Pause/stop all background audio when:

  * app is minimized
  * app goes to background
  * app is closed
  * user exits game

Use proper Flutter lifecycle handling:

* WidgetsBindingObserver
* AppLifecycleState

Resume music only when app returns to foreground if appropriate.

---

## Final Requirement

After implementing all fixes:

* Test navigation
* Test Firebase login flow
* Test audio lifecycle
* Test rewarded ads
* Test block placement repeatedly
* Test app restart/reopen behavior

Do NOT break existing gameplay systems, animations, Firebase integration, reward systems, or level progression.
