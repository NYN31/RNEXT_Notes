### There are 4 ways to navigate between routes in Next.js

- Using the \<Link> Component
- Using the useRouter hook (Client Components)
- Using the redirect function (Server Compnents)
- Using the native History API

# \<Link> Component
\<Link> is a built-in component that extends the HTML \<a> tag to provide prefeching and client-side navigation between routes.

There are few props in \<Link> tag:
- href = stgring or object
- replace = boolean [default `false`, will replace current history]
- scroll = boolean [default `true`, ]
- prefetch = boolean or null [Only enable in production]
- **Good to know:** `className` and `target="_blank"` can be added

<br />

```
<Link href="/dashboard">Dashboard</Link>
-------------------------------------------
// Navigate to /about?name=test
<Link
  href={{
    pathname: '/about',
    query: { name: 'test' },
  }}
>
  About
</Link>

```

### Few key notes

- If the child of Link is a custom component that wraps an \<a> tag, you must add `passHref` to Link [hurts sites accessibility and might effect SEO]
- If the child of Link is a functional component, in addition to using `passHref` and `legacyBehavior`, you must wrap the component in `React.forwardRef`
- Disable scrolling to the top of the page defining `scroll=false` in the \<Link> tag.

### useRouter() hook

The `useRouter()` hook allows to programmatically change routes inside client components

**Recommendation:** Use the \<Link> component for navigation unless you have a specific requirement for using `useRouter()`.

- router.push(href: string, { scroll: boolean })
- router.replace(href: string, { scroll: boolean })
- router.refresh(): making a new request on server, re-fetching data requests and re-rendering server components.
- route.back()
- route.forward()
