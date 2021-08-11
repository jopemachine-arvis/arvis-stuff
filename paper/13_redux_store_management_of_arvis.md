# About redux-store management of arvis

arvis use redux to manage states.

You can check this state on `redux/reducers/types.ts`.

## The things stored in redux

* Some global necessory hotkey

* Auto launch

* Customizable UI config values

* Debugging setting (which type of logs should be logged in `chrome-devtool`)

* Clipboard history

* Other detailed setting values

## How to dispatch action to other renderer process

redux-store are available on every renderer processes.

To maintain every process's redux-state up to date, arvis use `ipc/mainProcessEventHandler/config/dispatchAction.ts`.

This event handler is registered in main process.

If any redux-state is changed in some process, the process notify main process redux-state's change through ipc.

Then main process send this `action` to destination renderer process.

## How to persist redux state

To persist redux state, arvis use `redux-persist`, `redux-persist-electron-storage`.

This file are store as json file named `arvis-gui-config`, and loaded every time arvis starts up.

## How to handle upgrade redux's state schema

arvis validate redux states by comparing `config/initialState.ts` and current store's `states` at startup.

If there are difference points, arvis forced to terminate to reset redux store's state.

redux store's state reset is caused by replacing `arvis-gui-config` file.

By doing proper replacing `arvis-gui-config`'s key-value, state changes after arvis restarts.

At this time, user's customized values should not be changed.

For this, arvis makes `arvis-redux-store-reset` file to write user's custom setting values before restart.

## Values not stored in redux

arvis does not store below setting values

* If search window is pinning, clipboard is pinning

=> arvis doesn't consider these states should be saved because arvis consider `pin state` should be off defaultly.

* If preference window's spinner is spinning.

=> arvis does not store dynamically changing UI state in redux. I think saving these states doesn't make sense.

* Extension's informations

Extension's informations are not saved in redux for the following reasons:

1. Extension's informations could be too big to save one file if the user use a lot of extensions.

2. Extension's informations is no need to be state. So it's just loaded on memory as form of Record object by arvis-core.

3. arvis-core's logic should be independent from redux logic