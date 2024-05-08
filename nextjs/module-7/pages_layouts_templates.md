# Pages:

### A page is UI that is unique to a route.

Good to know:

- The .js, .jsx, or .tsx file extensions can be used for Pages.
- A page is always the leaf of the route subtree.
- A page.js file is required to make a route segment publicly accessible.
- Pages are Server Components by default, but can be set to a Client Component.
- Pages can fetch data.


# Layouts:

### A layout is UI that is shared between multiple routes. On navigation, layouts preserve state, remain interactive, and do not re-render. Layouts can also be nested.

Good to know:

- Only the root layout can contain html and body tags.
- Layout by default server component
- Layouts do not have access to pathname. But imported Client Components can access the pathname using usePathname hook.
- You can use Route Groups to opt specific route segments in and out of shared layouts.
- You can use Route Groups to create multiple root layouts.


# Templates

### Similar to layouts. The Only difference is that templates create a new instance for each of their children on navigation. 

Use cases on navigation:
- To resynchronize useEffect
- To reset the state of child client components