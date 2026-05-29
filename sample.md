
---

### Part 2: Step-by-Step Setup in IntelliJ IDEA

Follow these steps exactly. This assumes you have **Node.js** installed on your computer.

#### Step 1: Create the Astro Project
1.  Open **IntelliJ IDEA**.
2.  Open the **Terminal** (`Alt + F12` or `View → Tool Windows → Terminal`).
3.  Run this command to create a new blog project:
    ```bash
    npm create astro@latest gate-cs-blog
    ```
4.  When asked:
    *   **Where?** Press Enter (current directory).
    *   **Template?** Choose **Blog** (or "Empty" if you want to build from scratch, but "Blog" gives you a head start).
    *   **Install dependencies?** Yes.
    *   **TypeScript?** Strict or Relaxed (your choice).
    *   **Git?** Yes.

#### Step 2: Install Math & Diagram Plugins
Astro needs specific plugins to render LaTeX and Mermaid.
1.  In the terminal, run:
    ```bash
    npx astro add markdown-remark
    ```
2.  Install the math and mermaid extensions:
    ```bash
    npm install remark-math rehype-katex rehype-mermaid
    ```

#### Step 3: Configure Astro (`astro.config.mjs`)
1.  Open the file `astro.config.mjs` in IntelliJ.
2.  Update it to look like this (this enables Math and Mermaid):

```javascript
import { defineConfig } from 'astro/config';
import remarkMath from 'remark-math';
import rehypeKatex from 'rehype-katex';
import rehypeMermaid from 'rehype-mermaid';

// https://astro.build/config
export default defineConfig({
  markdown: {
    remarkPlugins: [remarkMath],
    rehypePlugins: [
      rehypeKatex,
      [rehypeMermaid, { strategy: 'pre-mermaid' }]
    ],
  },
});