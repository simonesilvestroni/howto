# Common symbols

Columns in the tables:

* `Sym`: The symbol representing the key
* `Key`: The common name of the key
* `CrossPlat?`: Whether the symbol is cross-platform.  If "No", then the symbol is unlikely to render properly outside the Apple ecosystem.
* `Alt`: An alternate symbol used in some contexts (e.g., legacy)
* `Alt CrossPlat?`: Whether the alternate symbol is cross-platform

## Modifiers

When a key combination is displayed, the modifiers are written in the order presented here.  For example, <kbd>Control</kbd> + <kbd>Option</kbd> + <kbd>Shift</kbd> + <kbd>Command</kbd> + <kbd>Q</kbd> would be written as <kbd>⌃⌥⇧⌘Q</kbd>.

| Sym | Key         | CrossPlat? | Alt | Alt CrossPlat? |
|:---:|:------------|:----------:|:---:|:--------------:|
|  ⌃  | Control     |    Yes     |     |                |
|  ⌥  | Option      |    Yes     |     |                |
|  ⇧  | Shift       |    Yes     |     |                |
|  ⌘  | Command     |    Yes     |    |       No       |

The Command key was formerly represented by an Apple logo.  The Apple logo is one fo the few symbols here that can be easily typed with a typical keyboard layout: <kbd>⌥⇧K</kbd>

There is also an <kbd>Fn</kbd> modifier on modern Mac keyboards.  Typically, this isn't seen in keyboard shortcuts because it's primarily used to access keys <kbd>F1</kbd> through <kbd>F20</kbd>.  However, it can technically be combined with <kbd>Control</kbd> plus one other key to get a unique legacy combination.  Each of these <kbd>Fn</kbd> + <kbd>Control</kbd> combinations maps to a character in Unicode's U+F700 to U+F7FF private use range.  Some programs will erroneously print these characters upon receiving such a combination.  With system Mac fonts, these characters lack visible glyphs and are for internal use only.  Quote from `ftp://ftp.unicode.org/Public/MAPPINGS/VENDORS/APPLE/CORPCHAR.TXT`:

> NeXT's OpenStep reserved corporate characters in the range 0xF700 to
> 0xF8FF for transient use as keyboard function keys. The ones actually
> assigned in NextStep are 0xF700-0xF747, as follows. These are still
> used in the Mac OS X AppKit frameworks. Note that there is no glyph
> associated with these, and they are not mapped or used by the Mac OS
> Text Encoding Converter.

## Normal

| Sym | Key         | CrossPlat? | Alt | Alt CrossPlat? |
|:---:|:------------|:----------:|:---:|:--------------:|
|  ⎋  | Escape       |    Yes     |     |                |
|  ⏏  | Eject        |    Yes     |    |       No       |
|  ⌦  | Delete fwd   |    Yes     |     |                |
|  ⌫  | Delete       |    Yes     |     |                |
|  ⇪  | Caps lock    |    Yes     |     |                |
|  ←  | Left         |    Yes     |     |                |
|  →  | Right        |    Yes     |     |                |
|  ↑  | Up           |    Yes     |     |                |
|  ↓  | Down         |    Yes     |     |                |
|  ↩  | Return       |    Yes     |     |                |
|  ❘⃝ | Power        |     No     |     |                |
|  ⇞  | Page up      |    Yes     |     |                |
|  ⇟  | Page down    |    Yes     |     |                |
|  ⇤  | Back tab     |    Yes     |     |                |
|  ⇥  | Tab          |    Yes     |     |                |
|  ↘  | End          |    Yes     |     |                |
|  ↖  | Home         |    Yes     |     |                |
|  ⌤  | Enter        |    Yes     |  ⌅  |      Yes       |
|    | Context menu |     No     |     |                |
|  ⌧  | Clear        |    Yes     |     |                |
|  ␣  | Space        |    Yes     |  ␢  |       No       |
|  ⇭  | Num lock     |    Yes     |     |                |

The alternate eject symbol,  (U+F804), is from a Unicode private use region.  Apple designates it for use with mapping to/from the Mac OS Keyboard encoding.  Ideally, the official Unicode variant should be used instead, as it will be compatible with fonts on other platforms.  Quote from ftp://ftp.unicode.org/Public/MAPPINGS/VENDORS/APPLE/CORPCHAR.TXT:

> The following (11) are for mapping the Mac OS Keyboard and Mac OS Korean
> encodings (for Mac OS Korean also see 0xF83D, 0xF840-0xF84F).

# Complete list

Reference: ftp://ftp.unicode.org/Public/MAPPINGS/VENDORS/APPLE/KEYBOARD.TXT

These are the official Unicode symbol mappings published by Apple.

| Sym | Unicode | Mac  | Key name | Notes |
|:---:|:--------|:-----|:---------|:------|
|  ⇧  | U+21E7  | 0x05 | Shift
|  ⌃  | U+2303  | 0x06 | Control
|  ⎈  | U+2388  | 0x8A | Control | ISO
|  ⌥  | U+2325  | 0x07 | Option
|  ⎇  | U+2387  | 0x8B | Alt
|  ⌘  | U+2318  | 0x11 | Command
|    | U+F8FF  | 0x14 | Command | Old; solid Apple logo
|   | U+F8FF U+F87F | 0x6C | Command | Old; outlined Apple logo
|  ⇥  | U+21E5  | 0x02 | Tab right (LTR)
|  ⇤  | U+21E4  | 0x03 | Tab left (RTL)
|  ⌤  | U+2324  | 0x04 | Enter
|  ␣  | U+2423  | 0x09 | Space
|  ↩  | U+21A9  | 0x0B | Return (LTR)
|  ↪  | U+21AA  | 0x0C | Return (RTL)
|  ⌫  | U+232B  | 0x17 | Delete left (LTR)
|  ⌦  | U+2326  | 0x0A | Delete right (RTL)
|  ⎋  | U+238B  | 0x1B | Escape
|  ⌧  | U+2327  | 0x1C | Clear
|  ␣  | U+2423  | 0x61 | Blank
|  ⇪  | U+21EA  | 0x63 | Caps lock
|  ?⃝ | U+003F U+20DD | 0x67 | Help
|  →  | U+2192  | 0x65 | Right
|  ←  | U+2190  | 0x64 | Left
|  ↑  | U+2191  | 0x68 | Up
|  ↓  | U+2193  | 0x6A | Down
|  ↖  | U+2196  | 0x66 | Home
|  ↘  | U+2198  | 0x69 | End
|  ⇞  | U+21DE  | 0x62 | Page up
|  ⇟  | U+21DF  | 0x6B | Page down
|    | U+F803  | 0x6D | Context menu
|  ❘⃝ | U+2758 U+20DD | 0x6E | Power
|  ⏏  | U+23CF  | 0x8C | Eject
|  英数 | U+82F1 U+6570 | 0x8D | Eisu | Japanese
|  かな | U+304B U+306A | 0x8E | Kana | Japanese
|  F1 | U+F860 F 1 | 0x6F | F1
|  F2 | U+F860 F 2 | 0x70 | F2
|  F3 | U+F860 F 3 | 0x71 | F3
|  F4 | U+F860 F 4 | 0x72 | F4
|  F5 | U+F860 F 5 | 0x73 | F5
|  F6 | U+F860 F 6 | 0x74 | F6
|  F7 | U+F860 F 7 | 0x75 | F7
|  F8 | U+F860 F 8 | 0x76 | F8
|  F9 | U+F860 F 9 | 0x77 | F9
| F10 | U+F861 F 1 0 | 0x78 | F10
| F11 | U+F861 F 1 1 | 0x79 | F11
| F12 | U+F861 F 1 2 | 0x7A | F12
| F13 | U+F861 F 1 3 | 0x87 | F13
| F14 | U+F861 F 1 4 | 0x88 | F14
| F15 | U+F861 F 1 5 | 0x89 | F15
| F16 | U+F861 F 1 6 |      | F16
| F17 | U+F861 F 1 7 |      | F17
| F18 | U+F861 F 1 8 |      | F18
| F19 | U+F861 F 1 9 |      | F19
| F20 | U+F861 F 2 0 |      | F20
|  | U+F802  | 0x0F |
| ✓ | U+2713  | 0x12 |
| ◆ | U+25C6  | 0x13 |
| ⇣ | U+21E3  | 0x10 |
| ⇠ | U+21E0  | 0x18 |
| ⇡ | U+21E1  | 0x19 |
| ⇢ | U+21E2  | 0x1A |

Some entries are missing key names; these don't map to physical keys.

LTR indicates usage with left-to-right languages: that means text flows from left to right, such as in most Western languages.  RTL indicates the opposite.  Many keyboards have both Delete Left and Delete Right, regardless of text direction.

ISO indicates a symbol designated by an ISO standard.  ISO standard symbols aren't necessarily used by Mac.

Symbols composed of multiple Unicode characters are special in that they are treated as a single character on Mac, despite appearing as multiple symbols.  For most of the characters, this grouping is controlled by the first character, which is a Unicode private use character that is invisible on Mac.  The others use standard Unicode combining techniques.  Quote from https://www.unicode.org/Public/MAPPINGS/VENDORS/APPLE/KEYBOARD.TXT:

> The block of 32 characters 0xF860-0xF87F is for transcoding hints.
> These are used in combination with standard Unicode characters to force
> them to be treated in a special way for mapping to other encodings;
> they have no other effect.

***

Originally from [Zenexer/Mac Keyboard Symbols.md](https://gist.github.com/Zenexer/c5243c4216f1f8cd2251).

---

#macOS