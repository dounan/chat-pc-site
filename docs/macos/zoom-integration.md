---
layout: macos-docs
---

# Zoom Actions

Zoom actions enable ChatPC to automate your Zoom meetings, from creating new meetings to viewing, updating, and deleting existing meetings.

<img src="/images/docs/macos/zoom-integration/zoom-create-meeting.png" alt="zoom create meeting example" width="700" />

These actions can be combined with other ChatPC actions. For example, ChatPC can look at your Calendar to find an available time to schedule a meeting, as well as sending an invite email to the attendees after the Zoom meeting has been created.

![zoom create meeting and send email example](/images/docs/macos/zoom-integration/zoom-create-meeting-and-email.png)

## Adding Zoom actions

1. Follow the [Getting Started](/docs/macos/getting-started) guide to install the ChatPC and register for a ChatPC account.

1. Open ChatPC Settings > Actions > Zoom

1. Click the toggle to turn on Zoom actions

![zoom settings unauthorized view](/images/docs/macos/zoom-integration/zoom-settings-unauthorized.png)

1. Click "Authorize"

1. Your browser will open to a Zoom authorization page (you may have to sign-in to Zoom first).

![zoom oauth screen](/images/docs/macos/zoom-integration/zoom-settings-unauthorized.png)

1. Click "Allow"

1. Your browser will ask permission to open the ChatPC app.

![zoom oauth open ChatPC](/images/docs/macos/zoom-integration/zoom-oauth-open-chatpc.png)

1. Click "Allow"

1. ChatPC should open and you should see that Zoom is now authorized.

![zoom settings authorized view](/images/docs/macos/zoom-integration/zoom-settings-authorized.png)

1. Open the chat window (see the Getting Started guide if you don't know how) and try out the following prompt:

<div class="alert alert-secondary" role="alert">
  Create a zoom meeting tomorrow at 9am
</div>

## Temporarily turning off Zoom actions

1. To temporarily turn off Zoom actions, click the toggle ChatPC Settings > Actions > Zoom

1. Note that this will *not* revoke ChatPC's access to your Zoom account and allows you to easily turn the Zoom actions back on without having to re-authorize.

## Revoking acccess to Zoom

1. Open ChatPC Settings > Actions > Zoom

![zoom settings authorized view](/images/docs/macos/zoom-integration/zoom-settings-authorized.png)

1. Click "Revoke Access"

1. Your browser will open to your Zoom "Added Apps" page (you may have to sign-in to Zoom first).

![zoom settings authorized view](/images/docs/macos/zoom-integration/zoom-added-apps.png)

1. Click "Remove"

1. Go back to the ChatPC Settings window and turn off the toggle for Zoom actions

1. Note that prior conversations with Zoom actions will *not* be deleted.
