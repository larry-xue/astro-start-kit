# Astro Start Kit

```sh
npm create astro@latest -- --template with-tailwindcss
```

This project demonstrates the integration of [Astro](https://astro.build) with [Tailwind CSS](https://tailwindcss.com), [Alpine.js](https://alpinejs.dev), and [MDX](https://mdxjs.com).

## Features

- **Astro**: Fast, modern static site generator
- **Tailwind CSS**: Utility-first CSS framework
- **Alpine.js**: Lightweight JavaScript framework for adding interactivity
- **MDX**: Markdown for the component era
- **Content Collections**: Type-safe content management
- **Responsive Design**: Mobile-friendly layout with proper typography

## Getting Started

1. Clone this repository
2. Install dependencies:
   ```sh
   npm install
   ```
3. Start the development server:
   ```sh
   npm run dev
   ```
4. Open your browser and navigate to `http://localhost:4321`

## Project Structure

- `src/blog/`: MDX blog posts
- `src/components/`: Reusable components
  - `AlpineCounter.astro`: Demo Alpine.js counter component
  - `BlogPostList.astro`: Component to list blog posts
  - `Prose.astro`: Typography component for styling Markdown content
- `src/pages/`: Page components and routes
  - `blog/[...slug].astro`: Dynamic route for blog posts
- `src/styles/`: Global styles
- `src/layouts/`: Layout components
  - `main.astro`: Base layout with HTML structure and metadata
- `src/content.config.ts`: Content collection configuration

## Alpine.js Components

This project includes [Alpine.js](https://alpinejs.dev/), a lightweight JavaScript framework for adding interactivity to your HTML.

### Example Components

- **AlpineCounter**: A simple counter component demonstrating basic Alpine.js usage
  - Location: `src/components/AlpineCounter.astro`
  - Features: Increase, decrease, and reset counter

## MDX Content Collections

This project uses Astro's Content Collections API to manage MDX content in a type-safe way. The project implements the latest Astro v5 Content Collections API.

### Blog Posts

- **Location**: `src/blog/`
- **Schema**: Defined in `src/content.config.ts`
- **Required Fields**:
  - `title`: String
  - `description`: String
  - `pubDate`: Date

### How to Add a New Blog Post

1. Create a new `.mdx` file in the `src/blog/` directory
2. Add the required frontmatter:
   ```mdx
   ---
   title: "Your Blog Post Title"
   description: "A brief description of your blog post"
   pubDate: 2023-11-10
   ---
   
   Your content here...
   ```
3. Write your content using Markdown and JSX

## Layouts

The project includes a base layout component that provides the HTML structure for pages:

### Main Layout

- **Location**: `src/layouts/main.astro`
- **Features**: 
  - Basic HTML structure
  - Meta tags
  - Global CSS imports

```astro
---
import '../styles/global.css';
const { content } = Astro.props;
---

<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <title>{content.title}</title>
  </head>
  <body>
    <slot />
  </body>
</html>
```

## Typography

The project uses a custom `Prose` component that applies Tailwind's typography plugin styles to Markdown content. This ensures consistent and beautiful typography across all blog posts.

```astro
<Prose>
  <Content />
</Prose>
```

The `Prose` component includes responsive styling and dark mode support.

## How to Use

### Alpine.js Components

```astro
import AlpineCounter from '../components/AlpineCounter.astro';

<AlpineCounter />
```

### Content Collections (Astro v5)

```astro
import { getCollection, render } from 'astro:content';

// Get all blog posts
const blogPosts = await getCollection('blog');

// Render a specific blog post
const { Content } = await render(entry);
```

## Resources

- [Astro Documentation](https://docs.astro.build)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Tailwind Typography Plugin](https://tailwindcss.com/docs/typography-plugin)
- [Alpine.js Documentation](https://alpinejs.dev/start-here)
- [MDX Documentation](https://mdxjs.com/docs/)
- [Astro Content Collections](https://docs.astro.build/en/guides/content-collections/)
