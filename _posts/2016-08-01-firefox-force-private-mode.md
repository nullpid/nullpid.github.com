---
title:        "Firefox: Force private mode"
---

<p class="lead">Firefox is probably the best browser out there, but it has to be used in <em>private mode</em>, otherwise is just another one!</p>

One could start Firefox in private mode by simpling issuing in terminal the `firefox --private` command, but this is a little bit boring repeatedly task.

To make it easier for us let's tune it our way.

## Disclaimer

Although it is not nothing special, remember to backup whatever has to be changed before changing it. The following changes have been applied to Firefox@47.0 on Fedora@24, although it shall be consistent with most linux-based distros.

There may be different and better ways for achieving the same, this is only the way I did it.

## Making it persistent

Edit `/usr/bin/firefox` (as `root`) and add the `--private` flag to `MOZ_FIREFOX_FILE` variable (line 51):

```bash
MOZ_FIREFOX_FILE="firefox --private"
```

Save the file... Now, every time you open Firefox, it will open in private mode (fuck tracking!).

## Reverting

If you wish to revert the changes just replace the mentioned file with the backup you made. If you are an irreverent person and did not follow the suggestion on `disclaimer section`, you just have to remove the `--private` flag from mentioned variable (line 51):

```bash
MOZ_FIREFOX_FILE="firefox"
```

## Gotchas

As far as I can tell, opening Firefox in private mode this way, will not display the usually `mask icon`. I do not know exactly why this happens as I did not had the interest to check the reason. It's assumed we are navigating in private mode because the homepage is consistent.
