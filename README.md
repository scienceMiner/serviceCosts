# Service Costs PWA

A mobile-first Progressive Web App for tracking recurring services.

## Features

- Four-column service list: Service, Cost, Frequency, End Date
- Add, edit and delete services
- Monthly/yearly frequency
- Correct monthly-equivalent total
- XML is the canonical persisted data format
- Export XML backup
- Import XML backup
- iOS-safe responsive design
- PWA manifest and service worker
- Calendar-date handling avoids timezone date shifting

## Install

Serve the folder from HTTPS. GitHub Pages is suitable.

On iPhone:

1. Open the HTTPS site in Safari.
2. Tap Share.
3. Choose Add to Home Screen.
4. Launch the app from the Home Screen.

## Notifications

The static app includes a browser Notification fallback, but this is NOT a reliable background reminder mechanism on iOS.

For a reliable "1 day before EndDate" notification, the production version should use Web Push:
- iPhone Home Screen web app grants notification permission.
- The browser registers a push subscription.
- The application sends the service/end-date information to a server.
- The server schedules a push for 24 hours before EndDate.
- The service worker receives the push and displays the notification.

The XML schema does not need to change for this.

## XML format

```xml
<?xml version="1.0" encoding="UTF-8"?>
<services>
  <service>
    <name>Netflix</name>
    <cost>17.99</cost>
    <frequency>M</frequency>
    <endDate>2026-12-31</endDate>
  </service>
</services>
```
