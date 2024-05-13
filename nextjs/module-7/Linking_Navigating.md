### There are 4 ways to navigate between routes in Next.js

- Using the \<Link> Component.
- Using the useRouter hook (Client Components).
- Using the redirect function (Server Compnents).
- Using the native History API.

# \<Link> Component

\<Link> is a built-in component that extends the HTML \<a> tag to provide prefeching and client-side navigation between routes.

There are few props in \<Link> tag:

- href = stgring or object
- replace = boolean [default `false`, will replace current history]
- scroll = boolean [default `true`, ]
- prefetch = boolean or null [Only enable in production]
- **Good to know:** `className` and `target="_blank"` can be added.

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

### Scrolling to an `id`

```
<Link href="/dashboard#settings">Settings</Link>

// Output
<a href="/dashboard#settings">Settings</a>
```

### Few key notes

- If the child of Link is a custom component that wraps an \<a> tag, you must add `passHref` to Link [hurts sites accessibility and might effect SEO].
- If the child of Link is a functional component, in addition to using `passHref` and `legacyBehavior`, you must wrap the component in `React.forwardRef`.
```
  <Link href={href} passHref>
    <Custom />
  </Link>
```
- Disable scrolling to the top of the page defining `scroll=false` in the \<Link> tag.

# useRouter() hook

The `useRouter()` hook allows to programmatically change routes inside client components.

**Recommendation:** Use the \<Link> component for navigation unless you have a specific requirement for using `useRouter()`.

### useRouter() methods

- router.push(href: string, { scroll: boolean })
- router.replace(href: string, { scroll: boolean })
- router.refresh(): making a new request on server, re-fetching data requests and re-rendering server components.
- route.back()
- route.forward()

### useRouter events

- usePathname() [[to determine if a link is active or not](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#checking-active-links)]
- useSearchParams()
- **Good to know:** This should be used in client components

### Disabling scroll rest

- By default next js will scroll to the top of the page when navigating to a new route. You can disable this behavior by passing `scroll: false` to `router.push()` or `router.replace()`.

# redirect function

For, Server Components, use the `redirect` function instead. It can be use also in Router handlers and server actions.

### Good to know

- `redirect` returns a 307 status code by default.
- For server action, it return 303 for success page as a result of POST request.
- In server actions and route handlers, `redirect` should be called after the try/catch.
- `redirect` function takes two parameters: redirect(path, type)
- redirect does not return any value.
- The `redirect` method uses a `307` by default, instead of a `302` temprorary redirect, meaning your requests will always be preserved as `POST` requests.
- If you'd like to redirect before the render process, use `next.config.js` or `Middleware`.


# Using the native History API

Next JS allow to use the native `window.history.pushState` and `window.history.replaceState` methods to update the browser's history stack without reloading the page.

# How Route and Navigation works

- **Code splitting:** Server component allow to automatically code-split by route segments.
- **Prefeching:** Prefetching is a way to preload a route in the background before the user visits it.
  
  - \<Link> componet: Automatically 
  - router.prefetch(): Programmatically

- **Caching:** Next JS has In-memory client-side cache called Router Cache. 
- **Partiall rendering** etc.
