# Olvid WebRTC for Android

[Olvid](https://olvid.io/) is a private and secure end-to-end encrypted messenger.

This repository contains what is required to publish a patched version of WebRTC, as used in the [Android Olvid application](https://github.com/olvid-io/olvid-android), to Maven Central repository.


# What was changed

Compared to the original WebRTC implementation, our patched version adds:
- support for HTTP/HTTPS proxy, which was present in old versions of WebRTC but was dropped,
- the possibility to configuration of a custom User-Agent.
 
The contents of the patch can be found in the github reposition of the Android Olvid application, [here](https://github.com/olvid-io/olvid-android/tree/main/obv_messenger/libwebrtc). The release versions for this library are aligned with the WebRTC build numbers as seen on [Chromium dash](https://chromiumdash.appspot.com/branches).


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
