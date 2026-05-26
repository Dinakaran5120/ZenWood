You are a senior game developer and software engineer.
Analyze my existing game codebase completely and implement the following fixes and improvements in a production-ready way without breaking existing functionality.

GAME LOGIC REQUIREMENTS

1. SCORE SYSTEM FIX

* Score should NOT increase when placing blocks on the board.
* Score should ONLY increase when rows or columns are cleared/blasted.
* Each blasted block should give exactly 5 points.
* Example:

  * if 4 blocks are blasted = 20 points
  * if 10 blocks are blasted = 50 points
* Ensure score updates correctly everywhere:

  * gameplay screen
  * levels page
  * store page
  * persistent storage/save data
* Remove all old score increment logic tied to block placement.

2. BLOCK SHAPE CONSISTENCY FIX

* Sometimes the block shape changes unexpectedly after placement.
* Fix the issue completely.
* The block shape preview and the placed block must always remain identical.
* Ensure:

  * no mutation bugs
  * no reference/state corruption
  * shape rotation/state consistency
* Add proper validation and state isolation to prevent future inconsistencies.

3. NEXT LEVEL BOARD RESET

* Whenever user moves to the next level:

  * clear the entire board/grid completely
  * reset all temporary gameplay states
  * no old blocks should remain
* Ensure level transitions are smooth and bug-free.

4. REMOVE SCORE FROM BLOCK PLACEMENT

* Double-check entire codebase and ensure:

  * placing blocks never increases score
  * ONLY blast/clear events increase score.

5. LEVEL & TIMER SYSTEM

* Starting from Level 10:

  * enable countdown timer.
* Initial timer:

  * 60 minutes.
* Difficulty should increase progressively for each level.
* Levels should support infinite progression architecture.
* Initially implement first 50 handcrafted/generated levels.
* After Level 50:

  * if user tries to swipe/navigate further,
  * show message:
    "Coming Soon"
* Ensure level progression system is scalable and production-ready.

6. AUTO-GENERATED LEVELS AFTER LEVEL 50

* Implement procedural/dynamic level generation system after Level 50.
* Generated levels should:

  * increase difficulty gradually
  * introduce new patterns/features
  * avoid repetition
  * remain playable and balanced
* Use scalable architecture for future level expansion.

7. SOUND SYSTEM IMPLEMENTATION
   Implement complete game audio feedback system.

Required sounds:

* block placement sound
* row/column clear blast sound
* button click sound
* level complete sound
* game over sound

Requirements:

* low latency playback
* no overlapping audio glitches
* centralized audio manager/service
* mute/unmute support
* volume handling support
* optimized for mobile performance

PRODUCTION REQUIREMENTS

* Refactor messy logic where necessary.
* Avoid hacks or temporary fixes.
* Ensure maintainable architecture.
* Remove duplicate logic.
* Optimize performance.
* Prevent memory leaks.
* Ensure smooth gameplay on mobile devices.
* Add proper comments where necessary.
* Maintain clean state management.
* Ensure persistence/save system works correctly.
* Ensure no regressions in existing features.

TESTING REQUIREMENTS

After implementation:

* verify scoring logic
* verify timer logic
* verify level transitions
* verify sound triggers
* verify procedural levels
* verify board reset behavior
* verify shape consistency
* verify persistence/save state
* test edge cases thoroughly

Finally:

* provide clean updated code
* explain major fixes implemented
* explain architecture improvements
* mention any assumptions made
* ensure the final implementation is production-ready.
