This repository is a quick prototype of the `svelte-headless-ui` library. [Here's the documentation](https://svelte-headlessui.goss.io/docs/2.0).

### Dialog

Go to `/dialog` to see the dialog example.

Notes:

- `fixed inset-0` is necessary on both `Dialog` and `DialogOverlay`
- `DialogTitle` and `DialogDescription` are not required.
- The `transform` class on the `Dialog` contents is necessary to center the dialog.

### Popover

Go to `/popover` to see the popover example.

### Tabs

Go to `/tabs` to see the tabs example.

Notes:

- `TabPanel` is not required to show content. Instead I use a slot and navigate to a subpage.
