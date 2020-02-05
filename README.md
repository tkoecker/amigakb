# amigakb
Arduino Amiga keyboard interface

This is a bit of code that allows you to use Amiga hw keyboard as USB HID keyboard.
Useful for projects such as replacing Amiga internals with Raspberry.

---

Fork from jklof/amigakb adjusted for Vampire V4-SA
Changed to fit the key mapping of V4-SA

This should work with all Amiga keyboards that have their own controller (i.e. all keyboards except A600 and A1200):
- A500
- A1000
- A2000/A3000
- A4000/CD32
- CDTV

Changes:
- Merged in changes from https://forum.arduino.cc/index.php?topic=139358.90
- Changed Backslash, Hash and Help key mappings
- Added reset handling for keyboards without reset line (All supported except A500 keyboard)
- Removed caps lock special handling (for compensating differences between Amiga and USB keyboard protocols)

Building for V4-SA:
- Use Ardoino IDE v1.6.5-r5 (needed for the changes below - the last version before a refactoring of the USB stack)
- Apply the change from https://github.com/tkoecker/Arduino/commit/e6783cb5e4b7e1dc8abc4932b3e3543ad793c6ff to
  get an USB core that uses low-speed USB, with only one boot protocol keyboard HID device

TODO:
- Add reset handling for A500 keyboard (i.e. keyboard with reset line)
- Fix mapping of numpad '(' and ')' keys (Amiga keycodes 0x5a, and 0x5b) (these seem currently not to be available on V4)
- Maybe adjust the caps lock behavior in case the handling in V4 will change.
