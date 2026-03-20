---
title: Navigating the UI
description: Understand the AIVA interface layout, navigation tabs, sidebar, theme switching, and help resources.
---

# Navigating the UI

AIVA is organized around a persistent header with navigation tabs, an optional sidebar for chat history, and a central content area that changes based on the active section.

---

## Main Layout

The interface is divided into three regions:

### Header

The header bar runs across the top of every page and contains:

- **Navigation Tabs**: The primary way to move between sections (see below).
- **Theme Toggle**: Switch between light and dark mode using the palette button in the header.
- **Job Manager**: Opens a panel showing the status of all active and recent background jobs (uploads, annotations, parsing).
- **What's New**: A bell-style indicator that appears when there are unread platform announcements. Click to open the What's New modal.
- **Help**: Opens the Help modal with quick-reference information and links.
- **User Menu**: Access your profile settings, subscription upgrade, and sign-out option.

### Sidebar (Chat Mode)

When you are on the Chat page, a collapsible sidebar appears on the left side of the screen:

- **Expanded view**: Shows your full conversation history with titles, timestamps, and a search/filter capability. Click any conversation to reload it. Use the **New Conversation** button at the top to start fresh.
- **Collapsed view**: Displays a narrow icon strip with quick-access buttons for your recent conversations and a button to expand the full sidebar.

The sidebar is only visible on Chat pages. On other sections (Samples, Reports, Playbooks, API, etc.), the full width is given to the content area.

### Content Area

The main region below the header. Its contents change depending on the active navigation tab. For Chat, it fills the available space without scrolling (the chat manages its own scroll). For content-heavy pages like API documentation and Reports, the area becomes scrollable.

---

## Navigation Tabs

The primary navigation tabs appear in the header. The following tabs are available to all users:

| Tab | Description |
|-----|-------------|
| **Chat** | The AIVA assistant interface. Start conversations, ask questions about your data, run analyses. This is the default landing page after login. |
| **Samples** | Manage projects, upload files, browse and organize your genomic samples. |
| **Playbooks** | Browse, create, and share reusable analysis workflows (Skills marketplace). |
| **Reports** | Create and manage clinical reports with AI-assisted auto-fill. |

Administrators also see:

| Tab | Description |
|-----|-------------|
| **Audit Logs** | View the platform audit trail for compliance and troubleshooting. |
| **Admin** | User management, platform announcements, and system configuration. |

Additional sections accessible from within pages:

- **Analysis**: Reached by clicking "Analyze" on a sample. Opens the tertiary analysis workspace with category-based views.
- **API**: Accessed from the user menu in the top-right corner. Contains API documentation, key management, and MCP setup instructions.

!!! info "Active tab indicator"
    The currently active tab is highlighted with an accent-colored underline. If the AIVA agent is running in the background while you are on another tab, the Chat tab shows a subtle glow effect so you know a response is being generated.

---

## Theme Switching

AIVA supports both light and dark color schemes.

- Click the **palette button** in the header to toggle between light and dark mode.
- The platform also respects your operating system preference on first load. If your OS is set to dark mode, AIVA will start in dark mode automatically.
- Your theme choice persists across sessions.

---

## What's New Announcements

Platform updates and new feature announcements are delivered through the **What's New** modal:

- When there are unread announcements, a notification badge appears on the What's New icon in the header.
- On your first login after new announcements are published, the What's New modal opens automatically.
- Announcements are marked as read once you view them, and the badge clears.

---

## Help Modal

Click the **Help** icon in the header to open an overlay with:

- Quick-start guidance for common tasks.
- Links to key documentation sections.
- Information about available AI tools and capabilities.

---

## Responsive Design

AIVA adapts to different screen sizes:

- **Desktop**: Full tab labels with icons, expanded sidebar available in chat mode.
- **Mobile**: Tabs become a horizontally scrollable strip with compact labels. The sidebar collapses to save space.

!!! tip "Navigating on mobile"
    On smaller screens, swipe the navigation tab bar horizontally to reveal tabs that do not fit on screen.

---

## Next Steps

With the layout understood, upload your first genomic file:

[:octicons-arrow-right-24: Uploading Your First Sample](uploading-your-first-sample.md)
