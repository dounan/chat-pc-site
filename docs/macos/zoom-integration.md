---
layout: macos-docs
---

# Zoom Actions

Zoom actions enable ChatPC to automate your Zoom meetings, from creating new meetings to viewing, updating, and deleting existing meetings.

<img src="/images/docs/macos/zoom-integration/zoom-create-meeting.png" alt="zoom create meeting example" width="700" />

These actions can be combined with other ChatPC actions. For example, ChatPC can look at your Calendar to find an available time to schedule a meeting, as well as sending an invite email to the attendees after the Zoom meeting has been created.

<img src="/images/docs/macos/zoom-integration/zoom-create-meeting-and-email.png" alt="zoom create meeting and send email example" width="700" />

## Adding Zoom actions

1. Follow the [Getting Started](/docs/macos/getting-started) guide to install the ChatPC and register for a ChatPC account

1. **IMPORTANT: make sure you have the macOS Zoom app installed**

1. Open ChatPC Settings > Actions > Zoom

1. Click the toggle to turn on Zoom actions

<img src="/images/docs/macos/zoom-integration/zoom-settings-unauthorized.png" alt="zoom settings unauthorized view" width="700" />

1. Click "Authorize"

1. Your browser will open to a Zoom authorization page (you may have to sign-in to Zoom first).

<img src="/images/docs/macos/zoom-integration/zoom-settings-unauthorized.png" alt="zoom oauth screen" width="700" />

1. Click "Allow"

1. Your browser will ask permission to open the ChatPC app.

<img src="/images/docs/macos/zoom-integration/zoom-oauth-open-chatpc.png" alt="zoom oauth open ChatPC" width="700" />

1. Click "Allow"

1. ChatPC should open and you should see that Zoom is now authorized.

<img src="/images/docs/macos/zoom-integration/zoom-settings-authorized.png" alt="zoom settings authorized view" width="700" />

## Using Zoom actions

1. Open the chat window (see the Getting Started guide if you don't know how) and try out the following prompts in order:

<div class="alert alert-secondary" role="alert">
  Create a zoom meeting tomorrow at 9am
</div>

<div class="alert alert-secondary" role="alert">
  Update the meeting to 10am
</div>

<div class="alert alert-secondary" role="alert">
  Delete the meeting
</div>

## Temporarily turning off Zoom actions

1. To temporarily turn off Zoom actions, click the toggle ChatPC Settings > Actions > Zoom

1. Note that this will *not* revoke ChatPC's access to your Zoom account and allows you to easily turn the Zoom actions back on without having to re-authorize.

## Revoking acccess to Zoom

1. Open ChatPC Settings > Actions > Zoom

<img src="/images/docs/macos/zoom-integration/zoom-settings-authorized.png" alt="zoom settings authorized view" width="700" />

1. Click "Revoke Access"

1. Your browser will open to your Zoom "Added Apps" page (you may have to sign-in to Zoom first).

<img src="/images/docs/macos/zoom-integration/zoom-added-apps.png" alt="zoom settings authorized view" width="700" />

1. Click "Remove"

1. Go back to the ChatPC Settings window and turn off the toggle for Zoom actions

1. Note that prior conversations with Zoom actions will *not* be deleted.
