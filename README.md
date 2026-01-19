# Olvid WebRTC for Android

[Olvid](https://olvid.io/) is a private and secure end-to-end encrypted messenger.

This repository contains what is required to publish a patched version of WebRTC, as used in the [Android Olvid application](https://github.com/olvid-io/olvid-android), to Maven Central repository.


# What we changed in WebRTC

Compared to the original WebRTC implementation, our patched version contains some minor modifications:
- support for HTTP/HTTPS proxy,
- the possibility to configuration of a custom User-Agent.

This way, Olvid is able to issue secure audio & video calls using a TCP connection through a proxy on networks where UDP is blocked and a proxy is mandatory (note that, in the browser, WebRTC is able to do this, the APIs are simply not available in the Android version of the library).

The contents of the patches we apply can be found in the [`patches/`](patches/) folder. The release version numbers for this library are aligned with the WebRTC build numbers as seen on [Chromium dash](https://chromiumdash.appspot.com/branches).


# Building from the sources

This project only takes care of publishing to Maven Central, and contains a pre-compiled version of the WebRTC library that we update with (almost) every new stable release of WebRTC. Bundling pre-compiled open-source libraries in an open-source project is not usually considered good practice, but the effort required to compile WebRTC is such that we decided to make your life easier 😊

If you want to compile WebRTC yourself, you should follow the standard WebRTC build procedure, simply applying the provided patch:

- clone the `depot tools`
- fetch `webrtc_android`
- sync with `gclient`
- checkout the `branch-heads/xxxx` you want to compile
- **apply the Olvid patch available in the [`patches/`](patches/) folder corresponding to the `xxxx` version you chose** (you can use the `git apply olvid_xxxx.patch` command)
- compile with `build_aar.py`
 
Finally, in the main [`build.gradle`](https://github.com/olvid-io/olvid-android/blob/main/obv_messenger/app/build.gradle) file of Olvid for Android, replace the line:
```
implementation 'io.olvid.messenger:olvid-webrtc-android:xxxx'
```
with a line like 
```
implementation files('../libwebrtc.aar')
```
pointing towards your newly compiled aar.



# License

Olvid is licensed under the GNU Affero General Public License v3. The full license is available in [`LICENSE`](LICENSE).

    Olvid for Android
    Copyright © 2019-2026 Olvid SAS
    
    Olvid is free software: you can redistribute it and/or modify
    it under the terms of the GNU Affero General Public License, version 3,
    as published by the Free Software Foundation.
    
    Olvid is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU Affero General Public License for more details.
    
    You should have received a copy of the GNU Affero General Public License
    along with Olvid.  If not, see <https://www.gnu.org/licenses/>.
