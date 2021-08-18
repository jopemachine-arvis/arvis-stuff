# How hotkey feature works

Hotkey implementation is a little tricky.

For hotkey implementation, below three librarys are used.

* iohook
* use-key-capture
* electron/globalshortcut

## How to record key in hotkey record form

Key recording uses iohook.

iohook starts at renderering process.

(At first, I implemented iohook at main process, this occurs SIGILL force quit error when capslock key is pressed, So I moved iohook to renderer process.)

When the hotkey record form is mounted, keydown event handler of iohook is registered.

and when the form is unmounted, the handler is unregistered.

Because iohook keydown event handler only returns keycode, arvis translate this keycode to hotkey string before recording.

For this transformation, arvis use `utils/iohook/keyTbl`, `utils/iohook/keyUtils`

In `utils/iohook/keyTbl`, there is a table that shows the key code and key string of all available keys.

In `utils/iohook/keyUtils`, there are some utility function for translating keycode and hotkey string.

## Double key handling

Arvis support modifier double key.

For implementation of this, arvis use `hooks/utils/doubleKeyUtils`.

## How hotkey is registered (not double key)

Except for the double key, the other hotkeys are registered in `electron/globalshortcut`.

This process occurs after arvis start, some hotkeys are changed.

## How double hotkeys works

Registering double hotkeys is not supported in `electron/globalshortcut`, `iohook` both.

So iohook watchs all modifier key press in keydown event handler.

and use timers for each modifier keys, recognize double key press, when modifier key is pressed twice in a very short time.

For this, arvis uses `hooks/utils/useDoubleHotkey`.

Because iohook should exist in renderer process, double key press handlers exist in renderer process.

On the other hand, `electron/globalshortcut` should execute in main process.

So, after acquiring registered hotkey informations (from arvis-core, redux-store) in renderer process,

double keys are registered in renderer process right away, other key informations are sent to main process through ipc

## How default hotkey works

Some hotkeys should be executed only in renderer process.

For example, calling `large text window` only be possible on `search window`'s item.

Even if user press the hotkey, large text window should not shows up if the condition not meets.

So this hotkeys are not registered in separate hotkeys.

These hotkeys are handled by `use-key-capture`'s key down event handler.
