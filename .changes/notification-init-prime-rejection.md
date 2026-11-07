---
notification: patch
notification-js: patch
---

Fixed the initialization script surfacing a failed permission check as an unhandled promise rejection. The script is also injected into the webview's initial `about:blank` document, where the IPC request has an opaque origin and the app's capability does not apply, so `plugin:notification|is_permission_granted` is rejected there. The rejection is now ignored and `Notification.permission` keeps its `default` value until the script runs again on the real document.
