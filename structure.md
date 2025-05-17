# Project Directory Structure

This document outlines the main directory and file structure of the GenRec project.

## Root Directory (`/`)

-   `.gitignore`
-   `.gitmodules`
-   `.roomodes`
-   `.taskmasterconfig`
-   `.windsurfrules`
-   `package.json`
-   `package-lock.json`
-   `AST/` (Nested Astro Project/Module - See details below)
-   `Directus/`
    -   `data_model.md`
    -   `cursor_categories/`
        -   `categories.json`
    -   `cursor_recipes/`
        -   `mediterranean-veggie-halloumi-wrap.json`
        -   `spicy-chorizo-manchego-baguette.json`
        -   `tags.md`
        -   `test1.json`
        -   `the-gobbler-thanksgiving-leftover-sandwich.json`
        -   `ultimate-grilled-cheese.json`
-   `scripts/`
    -   `PRD.txt`
    -   `task-complexity-report.json`
-   `tasks/`
    -   `task_001.txt`
    -   `task_002.txt`
    -   `task_003.txt`
    -   `task_004.txt`
    -   `task_005.txt`
    -   `task_006.txt`
    -   `task_007.txt`
    -   `task_008.txt`
    -   `task_009.txt`
    -   `task_010.txt`
    -   `task_011.txt`
    -   `task_012.txt`
    -   `task_013.txt`
    -   `task_014.txt`
    -   `task_015.txt`
    -   `task_016.txt`
    -   `tasks.json`
    -   `tasks.json.bak`

## `AST/` Directory (Nested Project/Module)

**IMPORTANT REMINDER: All new frontend files and folders (components, pages, layouts, assets, etc.) for the main application MUST be created *within* this `AST/` directory and its subdirectories (e.g., `AST/src/components/`, `AST/src/pages/`). Avoid creating these in the root-level `src/` directory.**

-   `AST/`
    -   `.gitignore`
    -   `README.md`
    -   `astro.config.mjs`
    -   `package.json`
    -   `package-lock.json`
    -   `tsconfig.json`
    -   `public/`
        -   `favicon.svg`
    -   `src/`
        -   `assets/`
            -   `astro.svg`
            -   `background.svg`
        -   `components/`
            -   `Welcome.astro`
            -   `decor/` (Empty)
            -   `homepage/`
                -   `CategoryTagsNavigationSection.astro`
                -   `FeaturedRecipesSection.astro`
                -   `HeroSection.astro`
                -   `LatestBlogPostsSection.astro`
            -   `svelte/`
                -   `ColorFontTestIsland.svelte`
                -   `DetailedSandwichAssembly.svelte`
                -   `FeaturedSlider.svelte`
                -   `GsapTestBox.svelte`
                -   `HeroAnimation.svelte`
                -   `RecipeCard.svelte`
                -   `SandoHubLogo.svelte`
                -   `SandwichStacker.svelte`
                -   `TestIsland.svelte`
                -   `TopDownSandwichAssembly.svelte`
        -   `layouts/`
            -   `BaseLayout.astro`
            -   `components/`
                -   `Footer.astro`
                -   `Header.astro`
                -   `Navigation.astro`
        -   `pages/`
            -   `gsap-tests.astro`
            -   `index.astro`
            -   `style-tests.astro`
            -   `test-page.astro`
        -   `services/`
            -   `blogService.js`
            -   `directus.js`
            -   `directus.ts`
            -   `imageService.js`
            -   `recipeService.js`
            -   `tagService.js`
        -   `styles/`
            -   `main.scss`
            -   `base/`
                -   `_animations.scss`
                -   `_base.scss`
                -   `_reset.scss`
                -   `_typography.scss`
                -   `_utilities.scss`
                -   `_variables.scss`
            -   `components/`
                -   `.gitkeep`
                -   `_buttons.scss`
                -   `_cards.scss`
                -   `_dropdowns.scss`
                -   `_forms.scss`
                -   `_nav-buttons.scss`
                -   `_navigation.scss`
                -   `_todos.scss`
            -   `layouts/`
                -   `.gitkeep`
                -   `_grid.scss`
            -   `utils/`
                -   `_functions.scss`
                -   `_mixins.scss`

---
*This structure is based on a snapshot and should be updated as the project evolves.*
