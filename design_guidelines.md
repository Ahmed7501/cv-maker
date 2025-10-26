# AI-Powered CV Maker - Design Guidelines

## Design Approach Documentation

**Selected Approach:** Design System Approach with Fluent Design principles  
**Justification:** This is a utility-focused productivity tool where efficiency, clarity, and professional output are paramount. Users need to input data quickly, see immediate results, and generate polished CVs. The interface should feel like a professional design tool.

**Key Design Principles:**
- **Clarity over decoration** - Every element serves a functional purpose
- **Instant feedback** - Changes appear immediately in the preview pane
- **Professional polish** - The tool itself should reflect the quality users want in their CVs
- **Efficient workflows** - Minimize clicks and cognitive load

## Typography System

**Primary Font:** Inter (via Google Fonts)
- **Form Labels & UI Text:** 14px (text-sm), font-medium, tracking-tight
- **Input Fields:** 16px (text-base), font-normal
- **Section Headings:** 18px (text-lg), font-semibold
- **Page Title:** 24px (text-2xl), font-bold
- **Button Text:** 14px (text-sm), font-medium

**CV Template Fonts (for preview pane):**
- **Modern Template:** Inter for all text
- **Classic Template:** Georgia (serif) for headings, Inter for body
- **Creative Template:** Poppins for headings, Inter for body
- **Executive Template:** Playfair Display for name, Inter for content
- **Minimalist Template:** Inter with tighter tracking throughout

**Typography Hierarchy in CV Previews:**
- **Candidate Name:** 28-32px, font-bold
- **Section Titles:** 16-18px, font-semibold, uppercase tracking
- **Job Titles:** 14-16px, font-semibold
- **Body Text:** 11-12px, font-normal, leading-relaxed

## Layout System

**Main Application Structure:**
- **Desktop (≥1024px):** Split-screen with 40% form editor (left) and 60% preview (right)
- **Tablet (768px-1023px):** Stacked layout with tabbed navigation between "Edit" and "Preview"
- **Mobile (<768px):** Full-width stacked with floating "Preview" button

**Spacing Units (Tailwind):**
- **Micro spacing:** Use p-2, gap-2 for tight groupings (icon + label)
- **Standard spacing:** Use p-4, gap-4, m-4 for form fields, section padding
- **Section spacing:** Use p-6, gap-6 for major sections and cards
- **Large spacing:** Use p-8, gap-8 for top-level containers and separation

**Container Widths:**
- Form editor: max-w-2xl with px-6 internal padding
- CV preview: Fixed A4 aspect ratio (210mm × 297mm), scaled to fit viewport
- Preview container: bg-neutral-100 with p-8 to show "paper on desk" effect

## Component Library

### Primary Navigation Bar
- Fixed top bar, height 16 (h-16)
- Logo/title on left, "Export PDF" and "Load Example" buttons on right
- Subtle bottom border for definition
- Background with slight transparency/blur when scrolling

### Form Editor Panel (Left Side)

**Section Cards:**
- Each CV section (Personal Info, Summary, Experience, etc.) in expandable cards
- Card styling: rounded-lg, border, p-6
- Header with section icon, title, and collapse/expand control
- Hover state: subtle shadow elevation

**Input Fields:**
- Text inputs: Full width, rounded-md, border, px-4, py-3
- Text areas: min-h-32 for multi-line content
- Focus state: ring-2 with offset
- Labels: text-sm, font-medium, mb-2, placed above inputs

**AI Enhancement Buttons:**
- Positioned at top-right of text areas (Summary, Job Description fields)
- Small size (px-3, py-1.5), rounded-full
- Icon: sparkles/stars before text "Improve with AI ✨"
- Loading state: animated sparkle icon
- Subtle gradient background treatment

**Add/Remove Item Buttons:**
- For repeating sections (Experience, Education, Skills)
- "Add Experience" as primary button with icon
- "Remove" as text-only button with trash icon, appears on hover

### CV Preview Panel (Right Side)

**Preview Container:**
- White paper simulation (A4 ratio)
- Shadow: lg shadow for depth
- Border: 1px subtle border
- Zoom controls: Small floating toolbar with 75%, 100%, 125% options

**Template Selector:**
- Horizontal card carousel above preview
- Each template card: 120px wide, rounded thumbnails
- Active template: ring-2 border, slight elevation
- Template names below thumbnails: text-xs, font-medium

**CV Templates - Universal Elements:**
- All templates use 1.5-2cm margins for print safety
- Clean section dividers (horizontal lines or spacing)
- Consistent information hierarchy across templates
- Contact information prominently displayed

**Modern Template:**
- Left sidebar (30%) with personal info, skills
- Right content area (70%) with experience, education
- Accent line on sidebar edge

**Classic Template:**
- Center-aligned header with name and contact
- Single column, traditional layout
- Serif accents on section headers

**Creative Template:**
- Two-column asymmetric layout
- Color accent bars for section headers
- More playful spacing and alignment

**Executive Template:**
- Full-width header with large name typography
- Timeline-style experience section
- Professional, formal spacing

**Minimalist Template:**
- Ultra-clean, generous whitespace
- Thin dividing lines
- Compact information density

### Action Buttons

**Primary Actions (Export PDF):**
- px-6, py-3, rounded-lg
- font-medium, text-base
- Icon before text
- Prominent visual weight

**Secondary Actions (Load Example, Template Selection):**
- px-4, py-2, rounded-md
- Outlined or ghost variants
- Less visual weight than primary

**Tertiary Actions (Add item, collapse sections):**
- Text-only or icon-only
- Minimal styling, activated by proximity/hover

### Feedback & States

**Loading States:**
- Shimmer effect for AI processing
- Spinner for PDF generation
- Progress indication for multi-step processes

**Success Confirmations:**
- Subtle toast notifications (top-right)
- Green checkmark for AI improvements applied
- Brief confirmation for example data loaded

**Empty States:**
- Illustration or icon in preview when sections are empty
- Helpful text: "Add your first work experience above"
- Gentle encouragement to fill sections

## Animations

**Purposeful Motion Only:**
- Form-to-preview updates: No animation (instant update)
- Template switching: 200ms crossfade
- Section expand/collapse: 250ms height transition
- Button interactions: Standard hover states, no elaborate effects
- AI loading: Gentle pulse on sparkle icon

## Images

**No hero images required.** This is a productivity tool where the interface IS the product.

**Icons:**
- Use Heroicons (via CDN) throughout
- 20px (w-5, h-5) for inline icons
- 24px (w-6, h-6) for section headers
- 16px (w-4, h-4) for buttons and small UI elements

**Template Preview Thumbnails:**
- Generate simple mockups showing layout structure
- Use placeholder text/gray boxes to indicate content areas
- 120px × 150px dimensions

## Accessibility

- All form inputs have associated labels
- Focus indicators clearly visible on all interactive elements
- Keyboard navigation: Tab through form, Shift+Tab to reverse
- Screen reader announcements for AI improvements and actions
- Print view removes all chrome, maintains semantic HTML structure
- Sufficient contrast ratios for all text (WCAG AA minimum)

## Print-Specific Styling

- Hide all UI chrome (editor panel, buttons, template selector)
- CV preview scales to exact A4 dimensions
- Ensure page breaks don't split critical sections
- Black text on white background for optimal printing
- Remove shadows and decorative elements in print view