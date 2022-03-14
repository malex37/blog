# Building a blog 2: Electric boogaloo

Onwards!

Now for a quick and "dirty" approach to how to serve the files I'll use express and host it on heroku with a random(maybe) name, I don't really care what this service address is.

Publishing new entries will work somewhat like this

```
- Me (me of course)
- Repo (Git repo where all the markdown files will be originating from)
- PostService (the service that will return a markdown file)

     ┌──┐             ┌────┐                    ┌───────────┐     
     │Me│             │Repo│                    │PostService│     
     └┬─┘             └─┬──┘                    └─────┬─────┘     
      │ Commit new entry│                             │           
      │ ────────────────>                             │           
      │                 │                             │           
      │                 │ POST request to update route│           
      │                 │ ────────────────────────────>           
      │                 │                             │           
      │                 │             Pull            │           
      │                 │ <────────────────────────────           
      │                 │                             │           
      │                 │           Download          │           
      │                 │ ────────────────────────────>           
      │                 │                             │           
      │                 │                             │           
      │                 │   ╔════════╗                │           
══════╪═════════════════╪═══╣ profit ╠════════════════╪═══════════
      │                 │   ╚════════╝                │           
     ┌┴─┐             ┌─┴──┐                    ┌─────┴─────┐     
     │Me│             │Repo│                    │PostService│     
     └──┘             └────┘                    └───────────┘    

```
[See this in planttext](https://www.planttext.com/?text=POv12i8m44NtSugvW1V8GWgwSACKFK6nln1CCc4oiUJs6hgeuFOztkSFnIQr6WFH5NmuyXrP79yaHc-Si3AIQQEEkxv0vLKTtyJyqbWMhdcU3BI9VM6i8VnL7RAYP4dbDncbs0FwzayuFYC7QJGWpTzV7m00)

In theory this should make it so that when the blog repo gets updated the latest `.md` version gets automatically cloned into the service. If heroku lets me do that with exec in nodejs.

We'll see.