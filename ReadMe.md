<p align="center">
iPhone keyboard layouts experimenting with improved ergonomics
<br>
(using <a href="https://apps.apple.com/us/app/xkeyboard-custom-keyboard/id1440245962">xKeyboard</a> $app)
</p>

<p align="center">  
</p>


## Introduction
#### Disorganized list of design principles
  - no Capitalization in on-hold popup menus: ⇧ is more convenient, so this just wastes space <img src="./img/NoCap.jpg" height="48">
    - ❗ but a ↑gesture would work even better (not suppoted)
  - paired symbols at physically paired keys <img src="./img/Pairs.jpg" height="48">
  - Easy entry of similar symbols via circular entry (so that you can always return if you overtap), e.g.,
    - tap `-` key multiple times to cycle through hyphen-minus/en-dash/em-dash `-` `–` `–`: easy
    - tap `$` key multiple times to cycle through `$` `€` `₽` (hold for a longer list; change the rules to your 3 favorite currencies and replace the base key from `$` to your most frequently used, current layout uses `₽` as the base)
  - smaller Spacebar, it doesn't need to repeat the waste of physical keyboards and be huge
  - fixing typos is common, so <kbd>⌫</kbd> should be more convenient - left of 🖒thumb's resting place (mnemonic: move left to remove left char)

##### Punctuation
  - Quick punctuation entry via 2 taps of nearby keys:
    - <kbd>,</kbd><kbd>.</kbd> → `;` (visual mnemonic)
    - <kbd>.</kbd><kbd>,</kbd> → `:`
    - <kbd>,</kbd><kbd>=</kbd> → `?` (or <kbd>.</kbd><kbd>-</kbd>)
    - <kbd>.</kbd><kbd>=</kbd> → `!`
    - see `Environment`→`Input Rules` for the full list

##### Numpad
  - Dumb `1234567890` row placement replaced with a numpad-like table
    ```
    y₋ u₁ i₂ o₃ p₊
       h₄ j₅ k₆ l*
       b₇ n₈ m₉ "/
    ```
  - Quick single number entry without switching to a dedicated big layout via <kbd>,</kbd><kbd>U</kbd>… sequence
  - Quick continuous number entry: numpad "mode" remains active a long as the previous symbols is a number/numeric sign (`+-/` or figure␠ ` ` (TBD))
    - double ␠bar exist since you are unlikely to need two figure␠ `  ` in numeric entry

## Install

Zip contents of a subfolder (not the subfolder) inside [xKeyboard](./xKeyboard), change extension from `.zip` to `.xkeyboard`, copy to phone, and import from the app

## Modify

  - Sequence rules in `Environment\Environment.plist`, e.g., for `,.`→`;`
    ```xml
    <dict><key>type</key><integer>0</integer><key>input1</key>
    <string>,</string><key>input2</key>
    <string>.</string><key>output</key>
    <string>;</string></dict>
    ```


## Use

## Known issues

  - Per-layout word dictionaries are missing
  - iPad/horizontal versions are WIP

## xKeyboad limitations

  - ❗ Deal-breaker: no swipe input support
  - No swipe gesture support, so no ↑swipe to Capitalize
  - Text sliding via the top panel is too fast, users should be able to control speed and acceleration curve and type
  - No custom popup menu layout so you could have a 3⋅3 grid and
    - hold+swipe↘ to insert ◌̀
    - hold+swipe↙ to insert ◌́
    </br>for 2D-mnenomic entry of diacritics
    - Ideally the menu should be circlular with arbitray areas, also helps in precision: the farther you move the finger from the center, the bigger the activation area
    - This should also allow raising the limit of 10 keys
  - No way to have a more ergonomic ~hex-like key positioning, only strict|- grid is allowed
  - No convenient arbitrary symbol insert due to the lack of search, requiring adding limited symbol sets (see `🔣Chars` layout)
  - Dynamic rules and input rules
    - No way to delete the previous dynamic key, so while you can have an input rule converting <kbd>q</kbd><kbd>q</kbd> into inserting 😼, after pressing the first <kbd>q</kbd> your layout won't change to indicate that the next <kbd>q</kbd> will insert a different symbol.
    - No way to move the caret so you could, with a single tap, insert `(⎀)` parenthesis and move text caret inside (or `‘⎀’`)
    - No way for dynamic keys/input rules to switch layers, e.g., <kbd>q</kbd><kbd>q</kbd> should be able to enable Emoji layer
    - No support for better text editing options: move/select/delete by word
    - Some functions are limited to the toolbar, e.g., copy/paste
  - Visual design
    - Superfluous key label in the key hold menu: if you needed the original key, you'd just tap it! You do the less ergonomic "hold" to insert other symbols
    - Keys with 2 labels suffer in legibility because you can't position labels at arbitrary location with arbitrary colors to differentiate between main key and alt keys: <div>✗ <img src="./img/KeyCap.png" height="24"> ✓</div>
    - Similarly, no custom button background prevents signalling that <kbd>,</kbd> is a special modifier-like key
    - Some symbols can't be displayed due to a lack of custom font support
    - No way to rename custom groups `1`,`2`,`3` of Keyboards at the top toolbar to indicate the actual layout that would change if you press them
  - Configuration is rather unergonomic:
    - Dynamic rule creation/editing: if you have a prefix rule that depends on 
      - 1–0 number being the prefix with
      - either of 3 chars after it
      </br> …good luck tapping those rules 30 time with multiple taps per each! As a workaround, you can copy&paste or edit it in the `.plist` layout directly if you setup a few of them. Or write your own rule-generating script.
    - No undo/redo/diff (list of edits and their effect), so making a mistake is costly (workaround: use a proper computer with version control to edit xKeyboard files as much as possible)
    - No quick way to enter `Keys` sets, currently need to enter layout edit, press a button, select key...
    - No multilingual support, requiring duplicating the whole keyboard instead of being able to set only some properties of a key (like the main key/label while leaving candidate symbols the same) and then have a dedicated "switch language" option
    - Awfully verbose XML: instead of a simple `+ t=0 , . ;` dynamic rule you need this (and this is already hand-optimized for readability, the default format is even worse)
      ```xml
      <dict><key>type</key><integer>0</integer><key>input1</key>
      <string>,</string><key>input2</key>
      <string>.</string><key>output</key>
      <string>;</string></dict>
      ```


## Credits
