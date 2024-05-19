# Loading UI

- The special file `loading.js` helps creating meaningful Loading UI with `React Suspense`. 
- Instant Loading State is a fallback UI that is shown immediately upon navigation.
- Fallback UI might be a spinner, a skeleton or a small but meaningful UI part.

### Good to know
 - Navigation is immediate, even with server-centric routing. 
 - Navigation is interruptible, meaning changing routes does not neet to wait for the content of the route to fully load before navigating to another route.
 - Shared layouts remain interactive while new route segments load.


# Streaming

Streaming with suspense - add loading.js file create Suspense boundaries

### With SSR following steps happend. 

- Fetch data on server
- Server render HTML Page 
- Server sent to client HTML, CSS and JS 
- A non-interactive user interface 
- react hydrates to make the interface interactive.

### Good to know

- SSR with react and next js helps improve the percieved loading performance by showing a non-interactive page to the user as soon as possible. 

- It still slow. So `Streaming` allow to break down the pages HTML to smaller chunks and progressivily send those chunk to the client. 


- This enables partgs of the page to be displayed sooner, without waiting for all the data to load before any UI can be rendered. 

- Streaming works well with Reacts component model because each component can be considered a chunk.

- Components that have higher priority or that don't rely on data can be sent first (e.g. layout), and React can start hydration earlier. Components that have lower priority (e.g. reviews, related products) can be sent in the same server request after their data has been fetched.

- Streaming particularly benefical to prevent long data request from blocking the page from rendering as it can reduce the TTFB and FCP. It also helps improve TTI especially on slower devices.