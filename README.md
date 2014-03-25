# sync-recentf

This package helps synchronizing the recent files list between emacs instances. Without it, each emacs instance manages its own recent files list. The last one to close persistently saves its list into `recentf-save-file`; all files recently opened by other instances are overwritten.

With `sync-recentf`, all running emacs instances periodically synchronize their local recent files list with `recentf-save-file`. This ensures that all instances share the same list, which is persistently saved across sessions.


## Installation

From `git`:

1. get this repository:

   ```sh
   $ git clone https://github.com/ffevotte/sync-recentf.git
   ```

2. add this to your init file:

   ```lisp
   (add-to-list 'load-path "/path/to/sync-recentf")
   (require 'sync-recentf)
   ```

## Setup

The synchronization actually happens when the recent files list is cleaned up (see `recentf-cleanup`), which by default happens only once at startup. You thus need to ensure that files list cleanup is done regularly, by setting `recentf-auto-cleanup` to a numeric value.

For example:

```lisp
;; Cleanup the recent files list and synchronize it every 60 seconds.
(setq recentf-auto-cleanup 60)

;; Activate recentf
(recentf-mode 1)
```


## Contributing

If you make improvements to this code or have suggestions, please do not hesitate to fork the repository or submit bug reports on [github](https://github.com/ffevotte/sync-recentf). The repository's URL is:

    https://github.com/ffevotte/sync-recentf.git


## License

Copyright (C) 2014 François Févotte.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program. If not, see <http://www.gnu.org/licenses/>.
