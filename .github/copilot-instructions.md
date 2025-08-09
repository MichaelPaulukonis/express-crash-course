# Copilot Instructions for Express Crash Course

## 1. Project Context

This is a simple "online crash course" web-app, served through basic html and css. No framework has been picked, and may not be needed.

## 2. Technology Stack

When suggesting code, please use the following technologies:

- HTML5
- CSS3
- JavaScript (vanilla)

## 3. Project Structure

Follow the creative coding architecture with clear separation:

**Core Application (`src/`):**
- Contains the core HTML, CSS, and vanilla JavaScript files for the web pages.

**Documentation (`docs/`):**
- **course.md**: The original high-level course outline.
- **course_expanded.md**: The detailed course outline with code snippets, resources, and tasks.
- **plans/**: Refactor plans and implementation outlines.
- **src/**: Notes on the app sources.

**Configuration:**
- Minimal configuration is expected for this project.

## 4. Coding Standards

1. **JavaScript:** Use standard JavaScript (ES6+) features.

2. **Naming Conventions:** Follow consistent naming conventions:
    - **Filenames:** `kebab-case` (e.g., `my-component.js`, `main-styles.css`)
    - **JavaScript Variables and Functions:** `camelCase` (e.g., `myVariable`, `calculateSum`)
    - **JavaScript Classes/Constructors:** `PascalCase` (e.g., `MyClass`, `UserConstructor`)


## 5. Mandatory Planning Process

**CRITICAL**: All development work must follow this planning process before any code implementation.

### 5.1 Plan-File Requirement

1. **Before Any Code Changes**  
   ALL feature requests, architectural changes, or significant modifications must begin with creating—or reusing—an appropriate plan-file in `docs/plans/`.

2. **User Confirmation Protocol**  
   When a user requests changes:

   1. **Inspect for Existing Plans**  
      - If you find one or more candidate files in `docs/plans/`, present:  
        > "I've found an existing plan-file (`NN.semantic-name.md`) that seems relevant.  
        > **Options:**  
        > 1. Update & use this plan  
        > 2. Draft a new plan-file  
        > 3. Proceed without a plan-file"  

   2. **Fallback to Creation Prompt**  
      - If no suitable candidate exists, ask:  
        > "No plan-file covers this change.  
        > **Options:**  
        > 1. Create a new plan-file now  
        > 2. Proceed without a plan-file"  

   3. **Honor the User's Choice**  
      - If they pick "proceed without…," continue directly to step 3 of the **Implementation Workflow**.  
      - Do **not** re-prompt on that same change request.

3. **Plan-File Naming Convention**  
   ```
   Format: NN.semantic-name.md or XA.semantic-name.md
   
   Examples:
   - 0A.drawing-modes-refactor.md (renamed historical plan)
   - 10.typescript-migration-plan.md (sequential numbering)
   - 15.offscreen-rendering-enhancement.md (current plan)
   
   Rules:
   - Two-digit prefix (01-99) for ordering, or XA for historical plans
   - Dot separator after number/letter combination
   - Kebab-case for semantic name
   - .md extension
   - Sequential numbering for chronological order
   - Use XA prefix for plans that pre-date e2e planning (temporal primacy indicator)
   ```

4. **Required Plan Contents**  
   - **Problem Statement**  
   - **Requirements** (functional & non-functional)  
   - **Technical Approach**  
   - **Implementation Steps**  
   - **Testing Strategy**  
   - **Risks & Mitigation**  
   - **Dependencies**

### 5.1.1 How to Plan Better

Our recent work has highlighted a few ways we can improve our planning process for the future:

1.  **More Thorough Upfront Analysis:** Before creating a plan, we should do a thorough analysis of the existing code that will be affected. This will help us to identify potential issues and to create a more robust plan from the start.
2.  **Consider the "What Ifs":** When creating a plan, we should try to consider all the possible "what ifs". For example, what if we want to add new features in the future? What if the user wants to undo an action? By considering these possibilities upfront, we can create a more flexible and extensible plan.
3.  **Embrace Non-Destructive Workflows:** As a general principle, we should try to embrace non-destructive workflows whenever possible. This will make our code more flexible and easier to maintain in the long run.
4.  **Iterate on the Plan:** It's okay to iterate on the plan as we learn more about the problem. Creating a separate analysis document, as we did with `zonal-analysis.md`, is a great way to do this. It allows us to correct the course of the project and to create a much better solution in the end.

5. **Exceptions and Scope**  
   - **Plan-file creation itself**  
   - **Documentation updates** (README tweaks, comments)  
   - **Minor bug fixes** (single-line or typo corrections)  
   - **All other significant work** requires a plan-file.

### 5.2 Implementation Workflow

1. **Detect or Create Plan**  
   - **Detect**: Scan `docs/plans/` for an existing relevant plan-file.  
   - **Create**: If none found (or user opts for a new file), generate `NN.semantic-name.md` with the required sections.  
2. **Review & Approve**  
3. **Implement Code**  
4. **Test** (per the plan's Testing Strategy)  
5. **Merge & Close Plan**

## 6. Copilot Guidance

### 6.1 Important Rules for All Occasions
- **Never assume missing context or make guesses. If any part of the request is unclear or ambiguous, ask the user for clarification before proceeding.**
- **Always specify the target file or files for any code or modification suggestions.**
- **Write modular, reusable code.** Split logic into distinct functions, classes, or modules as appropriate.
- **All code must be fully optimized:**  
  - Maximize algorithmic efficiency (runtime and memory).  
  - Follow project style conventions.  
  - Avoid unnecessary code and technical debt.
- **Do not agree with me by default.** Your role is to assist by providing the best technical guidance, even if it means constructively challenging my assumptions or requests.
- **When generating code, first outline your plan in pseudocode or comments, then provide the code.**  
  - Save these plans and any refactor documentation according to the Documentation section.
- **Keep responses concise and focused.** Use Markdown formatting for clarity.
- **After implementing new features or completing a refactoring task, ask the user if the documentation in `docs/` needs to be updated to reflect the changes.**
- **Never generate or suggest code that violates copyright or project policies.**

### 6.2. Shell Command Safety: Escaping Special Characters

**CRITICAL**: When using the `run_shell_command` tool, you **MUST** properly handle special characters within the `command` string to prevent shell injection vulnerabilities and command failures.

#### **Backticks (`)**

-   **Problem**: Unescaped backticks are executed as sub-commands by the shell.
-   **Rule**: You **MUST** escape each backtick with a double backslash (`\\`).
-   **Example**:
    -   **INCORRECT**: `git commit -m 'feat: add `thing`'`
    -   **CORRECT**: `git commit -m 'feat: add \`thing\`'`

#### **Single Quotes (')**

-   **Problem**: If the command string is enclosed in single quotes, any literal single quotes within it must be handled carefully.
-   **Rule**: To include a single quote inside a single-quoted string, you must end the string, add an escaped single quote (`\'`), and then start a new single-quoted string.
-   **Example**:
    -   **INCORRECT**: `echo 'It's a nice day'`
    -   **CORRECT**: `echo 'It'\''s a nice day'`





## 10. Testing Strategy

For this project, the testing strategy focuses on ensuring code quality, browser compatibility, and accessibility.

1.  **Linting:**
    -   **HTML:** Use `html-validate` for linting HTML files.
    -   **CSS:** Use `stylelint` for linting CSS files.
    -   **JavaScript:** Use `eslint` for linting JavaScript files.

2.  **Browser Compatibility:**
    -   **Automated Checks:** While full automation for all browser compatibility across a static site can be complex without a dedicated testing framework (e.g., Playwright, Cypress), basic checks can be integrated into CI/CD pipelines.
    -   **Manual Verification:** Regular manual testing across target browsers (Chrome, Firefox, Safari, Edge) is recommended.
    -   **Tools:** Consider services like BrowserStack or Sauce Labs for comprehensive cross-browser testing.

3.  **Accessibility (A11y) Checks:**
    -   **Automated Checks:** Integrate tools like `axe-core` (via CLI or browser extensions) into development workflows for automated accessibility audits.
    -   **Manual Verification:** Conduct manual accessibility reviews, including keyboard navigation and screen reader testing.
    -   **Guidelines:** Adhere to WCAG 2.1 AA guidelines.

## 11. Documentation Standards

1. **Component Documentation**: Use JSDoc for complex components:
   ```javascript
   /**
    * Grid drawing mode with customizable parameters
    * 
    * @param {Object} params - Grid parameters
    * @param {number} params.rows - Number of rows
    * @param {number} params.cols - Number of columns
    * @param {p5} p - p5.js instance
    */
   export const drawGrid = (params, p) => {
     // Implementation
   }
   ```

2. **Module Documentation**: Create concise overviews in `docs/src/`:
   - Optimize for AI-assisted development context
   - Mirror module folder structure
   - Focus on dependencies and interfaces

3. **Architecture Documentation**: Maintain in `docs/master.md` for project overview.

4. **Plan Documentation**: Save all refactor plans and implementation outlines in `docs/plans/`.


## 13. Commit Message Guidelines

All commit messages MUST follow the Conventional Commits specification.

-   **Format:** `<type>(<scope>): <description>`
-   **Common Types:** `feat` (new feature), `fix` (bug fix), `docs`, `style`, `refactor`, `test`, `chore`, `perf`.
-   **Breaking Changes:** Use `!` after the type/scope (e.g., `feat(api)!:`) or add a `BREAKING CHANGE:` footer for major version changes.

*Example:* `feat(zone): add unit tests for zone manipulation`

For changelog management and semantic versioning, see [Changelog Management Guidelines](./changelog-management.md)


## 14. Error Handling

For this static web application, error handling primarily focuses on client-side issues:

-   **JavaScript Errors:** All JavaScript errors should be logged to the browser's console for debugging purposes. User-facing error messages should be minimal and non-disruptive.
-   **Broken Links/Missing Assets:** Ensure proper handling of broken links and missing assets (e.g., custom 404 pages, graceful degradation).
-   **Client-Side Reporting:** For more complex scenarios, consider basic client-side error reporting mechanisms (e.g., simple `window.onerror` logging) if needed, but avoid overly complex solutions that introduce external dependencies.

## 15. Accessibility

Accessibility is a key consideration for this project. Adherence to WCAG 2.1 AA guidelines is encouraged.

-   **Semantic HTML:** Use appropriate HTML5 semantic elements (e.g., `<header>`, `<nav>`, `<main>`, `<article>`, `<aside>`, `<footer>`) to structure content and improve readability for assistive technologies.
-   **Keyboard Navigation:** Ensure all interactive elements are reachable and operable using only the keyboard (e.g., `Tab` key for navigation, `Enter`/`Space` for activation).
-   **Color Contrast:** Maintain sufficient color contrast ratios for text and interactive elements to ensure readability for users with visual impairments.
-   **Alternative Text for Images:** Provide meaningful `alt` attributes for all `<img>` tags to describe image content for screen reader users.
-   **Form Accessibility:** Ensure all form controls have associated `<label>` elements, and provide clear error messages and instructions.
-   **ARIA Attributes:** Use ARIA (Accessible Rich Internet Applications) attributes sparingly and correctly to enhance semantics where native HTML is insufficient (e.g., for custom widgets or dynamic content updates).

## 16. MCP Filesystem Path Conventions

**IMPORTANT**: The MCP filesystem server runs in a Docker container. This creates **two distinct path contexts**:

* **Host Path**: `/Users/michaelpaulukonis/projects/`
* **Container Path**: `/app/projects/`

### Use Rules

1. **User-Facing Output (Markdown, logs, etc.)**
   → Use **Host Paths** (`/Users/...`)

2. **Tool Arguments (`filesystem__*`)**
   → Use **Container Paths** (`/app/...`)

### Example:

* User says: "List the files in the `polychrome.p5` project."
* Internally: Map `/Users/.../polychrome.p5` → `/app/.../polychrome.p5`
* Tool call:
  `filesystem__list_directory(path='/app/projects/polychrometext.p5')`
* Respond:
  "Here are the files in `/Users/michaelpaulukonis/projects/polychrome.p5`:"

### 16.1. Filesystem Tool Selection: Local vs. Extra-Local

**CRITICAL**: You have access to two sets of filesystem tools: built-in tools (like `read_file`, `write_file`, `run_shell_command`) and MCP `filesystem__*` tools. You MUST use the correct toolset based on the file's location.

#### **Use Built-in Tools (Default)**

-   **When:** For ALL operations on files and directories **within** the current project's root directory (`/Users/michaelpaulukonis/projects/express_crash`).
-   **Why:** These tools are optimized for local project work and use the host's native file paths.
-   **Example:** To read `src/index.html`, you MUST use `read_file(absolute_path='/Users/michaelpaulukonis/projects/express_crash/src/index.html')`.

#### **Use `filesystem__*` MCP Tools (Exceptions)**

-   **When:** ONLY when you need to access files or directories **OUTSIDE** of the current project's root directory.
-   **Why:** The MCP server provides controlled access to the broader filesystem, which is otherwise sandboxed.
-   **Path Convention:** Remember to use the container path prefix (`/app/projects/...`) for all `filesystem__*` tool arguments.
-   **Example:** To read a config file from a sibling project, you MUST use `filesystem__read_file(path='/app/projects/another-project/config.json')`.


## 17. Dependencies and Environment

This project is designed to be framework-free and have minimal external dependencies. 

-   **Core Dependencies:** The primary dependencies are standard web technologies: HTML5, CSS3, and vanilla JavaScript.
-   **External Libraries:** Any external JavaScript or CSS libraries should be carefully evaluated for necessity and impact on performance and maintainability. When used, they should be included via CDN or directly in the project, avoiding complex package management systems unless explicitly introduced.
-   **Local Development Environment:** A modern web browser is sufficient for local development. No specific server environment (e.g., Node.js server) is required to serve the static files, though a simple local server (like Python's `http.server` or `live-server` npm package) can be used for convenience during development.
-   **Production Environment:** The project can be deployed to any static file hosting service (e.g., GitHub Pages, Netlify, Vercel).

---

**Note:** This file is for Copilot and other AI coding assistants only. Do not display to end users or include in documentation.
