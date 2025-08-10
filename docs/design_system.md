# Design System: CodeCraft/DevCourse

This document outlines the design system derived from the sample pages for the Express.js crash course. The goal is to create a consistent and reusable set of design patterns and components to be applied to the full course content.

## Philosophy

The design is modern, clean, and developer-focused. It uses a dark theme to reduce eye strain and a clear typographic hierarchy to ensure readability. The overall aesthetic is professional and engaging.

## I. Color Palette

The color scheme is based on a dark background with a vibrant blue accent color.

*   **Primary Background**: `#111418` (A very dark, almost black, blue-gray)
*   **Secondary Background**: `#1b2127` (A slightly lighter dark blue-gray, used for cards and highlighted sections)
*   **Primary Text**: `#ffffff` (White)
*   **Secondary Text**: `#9caaba` (A light, slightly desaturated blue-gray for less important text and footer links)
*   **Accent**: `#0d78f2` (A bright, vibrant blue for buttons and calls to action)
*   **Borders**: `#283039` and `#3b4754` (Dark blue-grays for subtle separation of UI elements)

## II. Typography

The typography is clean and modern, using a combination of sans-serif fonts to create a clear hierarchy.

*   **Primary Font**: "Space Grotesk" (Used for headings and prominent text)
*   **Secondary Font**: "Noto Sans" (Used for body text and paragraphs)
*   **Font Weights**: 400 (normal), 500 (medium), 700 (bold), 900 (black)

### Headings

*   **h1**: `text-4xl` (36px) or `text-5xl` (48px), `font-black`, `tracking-[-0.033em]`
*   **h2**: `text-lg` (18px) to `text-[22px]` (22px), `font-bold`, `tracking-[-0.015em]`
*   **h3**: `text-lg` (18px), `font-bold`, `tracking-[-0.015em]`

### Body Text

*   **p**: `text-base` (16px) or `text-sm` (14px), `font-normal`

## III. Components

### Buttons

*   **Primary Button**:
    *   **Background**: `bg-[#0d78f2]` (Accent blue)
    *   **Text**: `text-white`, `text-sm` or `text-base`, `font-bold`
    *   **Padding**: `h-10 px-4` or `h-12 px-5`
    *   **Border**: `rounded-lg`
*   **Secondary Button**:
    *   **Background**: `bg-[#283039]` (Dark blue-gray)
    *   **Text**: `text-white`, `text-sm`, `font-bold`
    *   **Padding**: `h-10 px-4`
    *   **Border**: `rounded-lg`

### Cards

*   **Background**: `bg-[#1b2127]`
*   **Border**: `border border-[#3b4754]`
*   **Padding**: `p-4`
*   **Corner Radius**: `rounded-lg`

### Header

*   **Background**: Transparent
*   **Border**: `border-b border-solid border-b-[#283039]`
*   **Padding**: `px-10 py-3`
*   **Layout**: `flex`, `items-center`, `justify-between`

### Footer

*   **Text Color**: `text-[#9caaba]`
*   **Layout**: `flex`, `flex-col`, `gap-6`, `text-center`

## IV. Layout

*   **Framework**: Tailwind CSS
*   **Structure**: The main layout is a full-height flex column. The content is centered with a `max-w-[960px]`.
*   **Spacing**: Consistent spacing is used throughout, with gaps of `3` to `8` units (e.g., `gap-3`, `gap-8`). Padding and margins are also applied consistently.
*   **Responsiveness**: The design uses container queries (`@container`) and responsive prefixes (`@[480px]:`) to adapt to different screen sizes.

## V. Iconography

The icons are SVGs embedded directly in the HTML. They are single-color and filled with `currentColor`, which means they inherit the color of the parent text element. This is a flexible and efficient way to handle icons.

## VI. Branding

The branding is inconsistent across the sample pages, with three different logos and brand names ("CodeCraft", "CodeCraft Academy", "DevCourse"). A single, consistent brand identity should be chosen and applied across all pages.

## VII. Content Elements

### Code Snippets

*   **Background**: `bg-[#0d1117]` (A very dark gray, slightly different from the primary background to create separation)
*   **Text**: A monospace font like "Fira Code" or "JetBrains Mono"
*   **Syntax Highlighting**: A color scheme that is consistent with the dark theme. We can use a library like Prism or highlight.js for this.
*   **Padding**: `p-4`
*   **Border**: `rounded-lg`

### Lists

*   **Unordered Lists** (`ul`):
    *   `list-disc`
    *   `pl-5` (for indentation)
*   **Ordered Lists** (`ol`):
    *   `list-decimal`
    *   `pl-5` (for indentation)
*   **List Items** (`li`):
    *   `mb-2` (for spacing between items)

### Inline Code

*   **Background**: `bg-[#283039]` (The same as the secondary button background)
*   **Text**: `text-[#9caaba]` (The secondary text color)
*   **Font**: A monospace font
*   **Padding**: `px-1.5 py-0.5`
*   **Border**: `rounded-md`