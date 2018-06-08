### Overview

The following configuration is for Android based Chrome/Chromium based Browsers. The list is different from the Desktop one because Android might have it's own flags or due to performance reasons there are changes made in order to not cripple your phone's performance.

#### Tested with

Chromium 67+


### Disabled (changed)

* #disable-webrtc-hw-decoding
* #disable-webrtc-hw-encoding
* #enable-webrtc-hw-vp8-encoding
* #clear-old-browsing-data
* #enable-usermedia-screen-capturing
* #disable-hyperlink-auditing
* #contextual-search-ml-tap-suppression
* #contextual-search-ranker-query
* #enable-password-generation
* #enable-manual-password-generation
* #wallet-service-use-sandbox
* #enable-chrome-home-survey
* #vr-browsing-native-android-ui
* #enable-gamepad-extensions
* #webxr
* #webxr-gamepad-support
* #webxr-orientation-sensor-device
* #webxr-hit-test
* #vr-icon-in-daydream-home
* #safe-search-url-reporting
* #keep-prefetched-content-suggestions
* #content-suggestions-debug-log
* #enable-breaking-news-push
* #interested-feed-content-suggestions
* #enable-ntp-article-suggestions-expandable-header
* #enable-ntp-remote-suggestions
* #enable-ntp-suggestions-notifications
* #PasswordExport
* #PasswordImport
* #password-search
* #enable-nostate-prefetch
* #enable-webfnc
* #enable-new-preconnect
* enable-async-dns
* #enable-mark-https-as set to: Enable (mark as actively dangerous) **this option will be removed**
* #BundledConnectionHelp
* enable-omnibox-voice-search-always-visible
* #enable-viz-test-draw-quad


### Enabled (changed)

* #enable-new-photo-picker (enabled)
* #enable-fast-unload
* #enable-history-entry-requires-user-gesture
* #smooth-scrolling
* #enable-quic (see explanation)
* #enable-android-spellchecker
* #enable-chrome-modern-design
* #enable-modal-permission-dialog-view
* #reduced-referrer-granularity
* #enable-site-per-process
* #offline-bookmarks
* #enable-brotli
* #force-show-update-menu-badge
* #tls13-variant set to: Enabled (Draft23)
* #disable-audio-support-for-desktop-share
* #enable-content-suggestions-new-favicon-server
* #important-site-in-cbd
* #enable-font-cache-scaling
* #new-audio-rendering-mixing-strategy
* #expensive-background-timer-throttling
* #modal-permission-prompts
* #lsd-permission-prompt
* #language-settings
* #enable-custom-context-menu
* #enable-custom-feedback-ui
* #omnibox-display-title-for-current-url
* #autoplay-policy set to: Document user activation required
* #enable-async-image-decoding
* #dont-prefetch-libaries
* #sound-content-setting
* #enable-parallel-downloading
* #enable-overflow-icons-for-media-controls
* #enable-downloads-location-change
* #enable-block-tab-unders
* #stop-in-background
* #clipboard-content-settings
* #enable-modern-media-controls
* #unified-consent


#### Obsolete flags 

* every v-sync specific settings are end-of-life