# Frontend

Frontends are written in golang and served by the golang http server. You will also need [node](https://nodejs.org/en) as a dev depedency for tailwind. HTMX is used to make the app interactive. Apps are server side rendered, Go will serve all the HTML and CSS required to render the page. The HTML is generated from Go using [templ](https://templ.guide). The CSS is generated from [Tailwind](https://tailwindcss.com/).

- [templ](https://templ.guide) for rendering the html fragments
- [htmx](https://htmx.org) for AJAX, CSS Transitions, WebSockets and Server Sent Events directly in HTML
- [air](https://github.com/cosmtrek/air) for building on code change
- [Tailwind](https://tailwindcss.com/) for styling, and [Prettier](https://prettier.io/) for formatting.
- [Make](https://www.gnu.org/software/make/) for making our lives simpler

## Why not ReactJS or Angular or something similar?

![Go](../img/htmx.jpg)

Thanks to Angelo Fallaria for this wonderful [image](https://twitter.com/angelo_fallaria/status/1747852397769269264?s=46&t=e4olOQNidU3pP6ZVlFOvIg)
