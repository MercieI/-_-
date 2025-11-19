# Design Guidelines - WAHA-Style Messaging Platform

## Design Approach
**System**: Custom dashboard design inspired by modern messaging/communication platforms (Slack, Discord, WhatsApp Web)
**Primary Focus**: Functional dashboard with clear information hierarchy and real-time status indicators

## Core Design Principles
- Clean, professional dashboard aesthetic
- Clear visual status communication through color
- Information density balanced with breathing room
- Technical tool for developers/operators (not consumer-facing)

## Color System
- **Sidebar Background**: Dark (#1E1E26 or #2A2A32)
- **Main Content**: Light neutral gray (#F5F5F7)
- **Primary Accent**: Blue (#3B82F6) for actions and highlights
- **Status Indicators**:
  - Green (#10B981): Connected/Operational
  - Yellow (#F59E0B): Waiting/Pending authentication
  - Red (#EF4444): Error/Disconnected
- **Log Severity**:
  - White/Gray: INFO
  - Yellow: WARN
  - Red: ERROR

## Typography
- **Font Family**: Inter or system sans-serif
- **Hierarchy**:
  - Section titles: text-lg font-semibold
  - Card headers: text-base font-medium
  - Body text: text-sm
  - Labels/metadata: text-xs text-gray-500

## Layout Structure

### Spacing System
Use Tailwind units: 2, 3, 4, 6, 8, 12 for consistent rhythm (p-4, gap-6, space-y-8, etc.)

### Main Layout
```
┌─────────────────────────────────────┐
│ [Sidebar] │ [Header]               │
│           ├─────────────────────────│
│ Sessions  │                         │
│ Messages  │  Main Content Area      │
│ Chats     │                         │
│ Webhooks  │                         │
│ Logs      │                         │
│ Settings  │                         │
│ API Docs  │                         │
└───────────┴─────────────────────────┘
```

## Component Library

### Sidebar Navigation
- Width: 64 (w-64)
- Dark background with white/gray text
- Icons from Heroicons (outline style)
- Active state: Left border accent + background highlight
- Hover: Subtle background lightening

### Session Cards
- Grid layout: grid-cols-1 md:grid-cols-2 lg:grid-cols-3
- White background, rounded-lg, shadow-sm
- Status dot (top-right): w-3 h-3 rounded-full
- Action buttons: Small, icon-based, grouped at bottom
- Display: Session name, status, last activity, message count

### Header Bar
- Height: 16 (h-16)
- Flex layout: justify-between items-center
- Left: Breadcrumb or section title
- Right: Language selector, theme toggle, user menu, "New Session" button

### QR Authentication Modal
- Centered modal: max-w-md
- White background, shadow-xl
- QR code: Large, centered (w-64 h-64)
- Instructions below QR
- Status text updates dynamically

### Message Console (Two-Column)
**Left Column** (60% width):
- Message bubbles with timestamps
- Incoming: bg-gray-100, rounded-tl-none
- Outgoing: bg-blue-500 text-white, rounded-tr-none
- Date separators: centered, text-xs, text-gray-400

**Right Column** (40% width):
- Composer at bottom
- Attachment buttons above text input
- Send button: bg-blue-500, rounded-full icon

### Chat View (Three-Panel)
- Left (25%): Chat list, scrollable
- Center (50%): Active conversation
- Right (25%): Contact details, collapsible

### Webhooks Table
- Clean table with borders
- Columns: Event, URL, Status, Last Attempt
- "Test" button per row
- Status badges: inline-flex rounded-full px-2 py-1 text-xs

### Logs Console
- Dark background (#1F2937)
- Monospace font (font-mono)
- Color-coded by severity
- Filters at top: Session, Date, Type
- Auto-scroll toggle

### Settings Panel
- Card-based sections
- Collapsible categories using disclosure pattern
- Form inputs grouped logically
- Save buttons per section

### API Explorer
- Accordion-style endpoint list
- Method badges: GET (green), POST (blue), DELETE (red)
- Expandable sections showing parameters, examples
- "Try it" button opens interactive form

## Animations
- Minimal, functional only:
  - Sidebar hover transitions: transition-colors duration-150
  - Modal fade-ins: transition-opacity
  - Status dot pulse for "connecting" state
  - NO elaborate scroll animations or unnecessary motion

## Icons
**Library**: Heroicons (outline for navigation, solid for actions)
- Navigation items: 20x20 icons
- Action buttons: 16x16 icons
- Status indicators: Use colored dots, not icons

## Images
**No hero images needed** - This is a functional dashboard/admin panel. All visual communication through UI components, tables, and status indicators.

## Key UI Patterns
- **Card Grid**: Sessions display in responsive grid
- **Split View**: Messages and Chats use divided layouts
- **Data Tables**: Webhooks use standard table structure
- **Modal Overlays**: QR authentication, confirmations
- **Console View**: Logs use terminal-style presentation
- **Accordion**: Settings and API docs use collapsible sections

## Responsiveness
- Sidebar: Collapsible on mobile (hamburger menu)
- Session cards: Stack on mobile (grid-cols-1)
- Chat view: Tabs on mobile (switch between list/conversation/details)
- Tables: Horizontal scroll on mobile with sticky first column