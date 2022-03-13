# Building a blog _from scratch_

I started thinking "I should have a blog" thinking if not for internet stardom it would give me a routine trigger, some personal improvement goals and a kind of journal. All the positives right?

Oh did I also mention it would keep my mind busy with non-work related problems? Yeah wins all around.

## Step 1: Build the blog

So onto building it. I don't _want_ to spend a lot of money, so the first approach I thought of was "I could use a simple express server, and serve static files" easy peasy, early 90s approach. This meant though that I had to either write a submitting UI of sorts **or** write every html file for a post _from scratch_, personal hell ensued.

### Error, try again
Alright, so obviously writing html 90s style is not a scalable approach, and writing a submitting UI means I'll have to worry about authentication and whatnot.

So now what? I have two basic requirements so far:
- Simple and effective, I want to write a post and submit in a simple manner.
- Not a ton of infrastructure

With those two combined I came up with a second approach (?)

![Prepare for trouble. Make it double](https://media1.giphy.com/media/37zCgyDV7pPos/giphy.gif)

To tackle the first I broke down in two, first what would allow me to write something for the web, simply, and with rich enough formatting. Here comes markdown to the rescue, it'll allow me to write simply, "in code" in the environments I already handle AND an important part, keep it in a version control.

## Step 2: ...?

So far I have how I'll write a post, but I don't have how I'll serve it...

Thinking this will be a low traffic site and a learning project it should be fine enough to render serve as a static file, which also adds the benefit of allowing me to test something to dynamically update/serve the posts with something like react and [remark](https://github.com/remarkjs/remark).

OK so far the "editing part" is going to be defined in markdown, and the site will be built with react. So..what am I building again?

Let's see it in a...diagram (janky plantuml style)
```
Guest (a reader)
Site (the actual blog)
Post Service (where the post are going to be served from)

     ┌─────┐                     ┌────┐                                ┌───────────┐
     │Guest│                     │Site│                                │PostService│
     └──┬──┘                     └─┬──┘                                └─────┬─────┘
        │Makes request to blog site│                                         │      
        │──────────────────────────>                                         │      
        │                          │                                         │      
        │    Returns react app     │                                         │      
        │<──────────────────────────                                         │      
        │                          │                                         │      
        │                          │   Requests a list of available posts    │      
        │                          │ ───────────────────────────────────────>│      
        │                          │                                         │      
        │                          │ Reads files available and provides info │      
        │                          │ <───────────────────────────────────────│      
        │                          │                                         │      
        │   Render list of posts   │                                         │      
        │<──────────────────────────                                         │      
        │                          │                                         │      
        │   Select post to read    │                                         │      
        │──────────────────────────>                                         │      
        │                          │                                         │      
        │                          │     Request markdown file to render     │      
        │                          │ ───────────────────────────────────────>│      
        │                          │                                         │      
        │     Render markdown      │                                         │      
        │<──────────────────────────                                         │      
        │                          │                                         │      
        │    Read rendered post    │                                         │      
        │──────────────────────────>                                         │      
     ┌──┴──┐                     ┌─┴──┐                                ┌─────┴─────┐
     │Guest│                     │Site│                                │PostService│
     └─────┘                     └────┘                                └───────────┘
```

Simple...right? We'll see how it goes

