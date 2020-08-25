# blog-template

This is a simple template to build a blog using [Nuxt.js](https://nuxtjs.org) and the [Content module](https://content.nuxtjs.org/). I built this for my friend who wants a blog but is too lazy to learn how to use Nuxt. <3

It uses [Tailwind](https://tailwindcss.com/) for styling.

## How to use

Fork this template, make changes to the styling, write some markdown posts, and upload to Netlify to get a cool blog!

## Styling

The template uses Tailwind, although if you want to add some normal CSS you can do so in the /assets/css/custom.css file.

The files you probably want to change are:

**/pages/index.vue**: Landing page

**/pages/about.vue**: About page

**/pages/blog/index.vue**: Blog post listing page

**/pages/blog/\_slug.vue**: Page used for the posts

## Writing Content

There's an [about.md](./content/about.md), where you can write details about yourself.

For blog posts, each file you create inside the `/content/blog/` folder will become a post. Check the Content module for more details about what you can do.

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# generate static project
$ npm run generate
```

## Setup in Netlify

Add a new site, and configure it with the following options:

**Branch to deploy**: master, or which-ever branch you prefer

**Build command**: npm run generate

**Publish directory**: dist

More information [here](https://nuxtjs.org/faq/netlify-deployment).
