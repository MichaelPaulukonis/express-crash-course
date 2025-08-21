
# Design System

This design system is based on the visual design of the Express.js Crash Course web pages. It provides a guide to the typographic, color, spacing, and component styles used throughout the application.

## 1. Typography

### Font Families
- **Primary:** "Space Grotesk", sans-serif
- **Secondary:** "Noto Sans", sans-serif

### Font Sizes and Weights

| Element | Font Size | Font Weight | Letter Spacing | Line Height |
|---|---|---|---|---|
| `h1` | 2.25rem (36px), 3rem (48px) | 900 (Black) | -0.033em | tight |
| `h2` | 1.25rem (20px), 1.5rem (24px) | 700 (Bold) | -0.015em | tight |
| `h3` | 1.125rem (18px), 1.25rem (20px) | 700 (Bold) | -0.015em | tight |
| Body | 0.875rem (14px), 1rem (16px) | 400 (Normal) | normal | normal |
| Button | 0.875rem (14px), 1rem (16px) | 700 (Bold) | 0.015em | normal |
| Link | 0.875rem (14px) | 500 (Medium) | normal | normal |

## 2. Spacing and Layout

The layout is built on a flexible grid system using Tailwind CSS utility classes. Spacing is based on a 4px grid unit.

### Grid System
- The main content area is centered with a `max-width` of `960px`.
- A container-based query system (`@container`) is used for responsive adjustments at different breakpoints.

### Margin and Padding
- **Common Padding:** `px-4`, `py-3`, `p-4`
- **Section Spacing:** `mb-6`, `py-5`, `py-6`
- **Gaps:** `gap-3`, `gap-4`, `gap-6`, `gap-8`

### Alignment
- Flexbox is used extensively for alignment, with `items-center` and `justify-between` being common patterns.

## 3. Components

### Buttons

- **Primary Button:**
  - **Background:** `#0d78f2`
  - **Text Color:** `#ffffff`
  - **Hover:** Darkens slightly
  - **Padding:** `h-10 px-4` or `h-12 px-5`
  - **Border Radius:** `rounded-lg`

- **Secondary Button:**
  - **Background:** `#283039`
  - **Text Color:** `#ffffff`
  - **Hover:** Darkens slightly
  - **Padding:** `h-10 px-4`
  - **Border Radius:** `rounded-lg`

- **Completed Button:**
    - **Background:** `#22c55e`
    - **Text Color:** `#ffffff`
    - **Hover:** `#16a34a`

### Navigation
- A horizontal navigation bar is present in the header.
- Links are styled as `text-white text-sm font-medium`.

### Cards
- **Lesson Item:**
  - A container with a title, description, and action buttons.
  - **Background:** `#1e2329` (for expanded content)
  - **Border Radius:** `rounded-lg`

- **Highlight Card:**
  - Used for course highlights.
  - **Background:** `#1b2127`
  - **Border:** `border border-[#3b4754]`
  - **Padding:** `p-4`
  - **Border Radius:** `rounded-lg`

### Containers
- **Main Layout Container:** `layout-container`
- **Content Container:** `layout-content-container`
- **Capstone Review Container:**
    - **Background:** `#1e2329`
    - **Padding:** `px-4 py-6`
    - **Border Radius:** `rounded-lg`

## 4. Color System

### Primary Colors
- **Blue:** `#0d78f2` (Primary actions, links, headers)

### Secondary Colors
- **Green:** `#22c55e` (Completed status)

### Background Colors
- **Primary:** `#111418` (Main background)
- **Secondary:** `#1e2329` (Content sections, cards)
- **Tertiary:** `#1b2127` (Highlight cards)

### Text Colors
- **Primary:** `#ffffff` (Headings, primary text)
- **Secondary:** `#9caaba` (Subheadings, descriptions)
- **Code:** `#e6db74`

### Border Colors
- **Primary:** `#283039`
- **Secondary:** `#3b4754`

### Gradients
- **Header Text:** `linear-gradient(90deg, #0d78f2 0%, #1e88e5 100%)`
- **Progress Bar:** `linear-gradient(90deg, #0d78f2 0%, #22c55e 100%)`
- **Hero Image:** `linear-gradient(rgba(0, 0, 0, 0.1) 0%, rgba(0, 0, 0, 0.4) 100%)`

## 5. Visual Hierarchy

- **Headings:** `h1`, `h2`, and `h3` are used to structure content with decreasing font size and weight.
- **Emphasis:** `<strong>` tags are used to highlight key terms with `text-white`.
- **Content Organization:** Content is organized into logical sections with clear headings and spacing.

## 6. Animation and Interaction

- **Hover States:** Buttons and links have hover effects that typically involve a change in background color.
- **Transitions:** `transition-colors` is used for smooth color changes on hover.
- **Lesson Content:** Lesson details are revealed/hidden with a click, managed by JavaScript.

## 7. Icons and Imagery

### Icons
- **Style:** Line icons are used throughout the application.
- **Library:** SVG icons are embedded directly in the HTML.
- **Color:** `currentColor` is used for icon fills, allowing them to inherit text color.
- **Size:** `20px`, `24px`

### Imagery
- **Hero Image:** A background image is used in the hero section of the main page.
- **User Profile:** A circular avatar is used for the user profile image.
