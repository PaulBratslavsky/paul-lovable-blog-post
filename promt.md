You are a senior frontend developer experienced with TypeScript, React, and building dynamic content-driven websites that consume Strapi RESTful APIs.

## Task

Build a blog platform frontend that consumes a Strapi v5 backend API.

## Critical Rule: Type-First Development

**BEFORE writing ANY code, you MUST:**

1. Review the actual API response examples below
2. Generate TypeScript interfaces matching the EXACT field names and structure
3. DO NOT assume, hardcode, or guess field names - derive everything from the actual API data

## Backend Configuration

**Use Base URL:** `https://inviting-cheese-ce66d3b9e0.strapiapp.com/api`

**Strapi v5 Response Format:**

- Collection types: `{ data: [...], meta: { pagination } }`
- Single types: `{ data: {...}, meta: {} }`
- Direct field access (no `.attributes` nesting)
- All relations and media auto-populated by backend

## Tech Stack

- React with TypeScript (strict mode)
- Tailwind CSS + shadcn/ui
- React Router
- `@strapi/client` - Strapi SDK
- `@tanstack/react-query` - Data fetching and caching

## API Endpoints & Real Response Examples

### 1. Global Settings (Single Type)

**GET** `https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/global`

```json
{
  "data": {
    "id": 2,
    "documentId": "wvghxjsle7i8yzhvnvjknec2",
    "title": "Global Page",
    "description": "It will be responsible for our header and footer data.",
    "createdAt": "2025-03-17T01:03:32.228Z",
    "updatedAt": "2025-03-19T03:16:37.847Z",
    "publishedAt": "2025-03-19T03:16:37.859Z",
    "banner": {
      "id": 2,
      "isVisible": true,
      "description": "Build APIs fast that your non technical user manage.",
      "link": {
        "id": 9,
        "href": "https://strapi.io",
        "label": "Learn More About Strapi",
        "isExternal": true,
        "isButtonLink": false,
        "type": null
      }
    },
    "header": {
      "id": 2,
      "logo": {
        "id": 6,
        "label": "My Website",
        "href": "/",
        "isExternal": false,
        "image": {
          "id": 1,
          "documentId": "cf68rcuc0dy4e6nw7dhhmg8q",
          "alternativeText": null,
          "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/logo_f375018201.svg"
        }
      },
      "navItems": [
        {
          "id": 10,
          "href": "/",
          "label": "Home",
          "isExternal": false,
          "isButtonLink": false,
          "type": null
        },
        {
          "id": 11,
          "href": "/about",
          "label": "About",
          "isExternal": false,
          "isButtonLink": false,
          "type": null
        },
        {
          "id": 12,
          "href": "/blog",
          "label": "Blog",
          "isExternal": false,
          "isButtonLink": false,
          "type": null
        }
      ],
      "cta": {
        "id": 13,
        "href": "https://strapi.io",
        "label": "Learn More",
        "isExternal": true,
        "isButtonLink": true,
        "type": "PRIMARY"
      }
    },
    "footer": {
      "id": 2,
      "text": "All rights reserved.",
      "logo": {
        "id": 7,
        "label": "My Website",
        "href": "/",
        "isExternal": false,
        "image": {
          "id": 1,
          "documentId": "cf68rcuc0dy4e6nw7dhhmg8q",
          "alternativeText": null,
          "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/logo_f375018201.svg"
        }
      },
      "navItems": [
        {
          "id": 14,
          "href": "/",
          "label": "Home",
          "isExternal": false,
          "isButtonLink": false,
          "type": null
        },
        {
          "id": 15,
          "href": "/about",
          "label": "About",
          "isExternal": false,
          "isButtonLink": false,
          "type": null
        },
        {
          "id": 16,
          "href": "/blog",
          "label": "Blog",
          "isExternal": false,
          "isButtonLink": false,
          "type": null
        }
      ],
      "socialLinks": [
        {
          "id": 8,
          "label": "Instagram",
          "href": "https://instagram.com",
          "isExternal": true,
          "image": {
            "id": 2,
            "documentId": "bw4q19jgutc9z0q5uota0knm",
            "alternativeText": null,
            "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/instagram_d5639475b1.svg"
          }
        },
        {
          "id": 9,
          "label": "Facebook",
          "href": "https://facebook.com",
          "isExternal": true,
          "image": {
            "id": 3,
            "documentId": "v15ebnh6pqxfvzsfk48vq23p",
            "alternativeText": null,
            "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/facebook_light_green_400ae69d80.svg"
          }
        },
        {
          "id": 10,
          "label": "Twitter",
          "href": "https://twitter.com",
          "isExternal": true,
          "image": {
            "id": 4,
            "documentId": "bg7iv0id9qqsn9w28er81jqy",
            "alternativeText": null,
            "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/twitter_d27e7ac06e.svg"
          }
        }
      ]
    }
  },
  "meta": {}
}
```

Generate routes based on the navigation.

### 2. Landing Page (Single Type)

**GET** `https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/landing-page`

Note: The landing page contains a `blocks` array with dynamic zone components. Each block has a `__component` field that identifies its type.

```json
{
  "data": {
    "id": 2,
    "documentId": "cehs2lhab5py2pgvnmsky85o",
    "title": "Landing Page",
    "description": "This is the main website page.",
    "createdAt": "2025-03-23T04:02:01.879Z",
    "updatedAt": "2025-08-03T01:07:23.472Z",
    "publishedAt": "2025-08-03T01:07:23.487Z",
    "blocks": [
      {
        "__component": "blocks.hero",
        "id": 2,
        "heading": "Build & Launch without problems",
        "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque efficitur nisl sodales egestas lobortis.",
        "links": [
          {
            "id": 21,
            "href": "https://strapi.io",
            "label": "Get Started",
            "isExternal": true,
            "isButtonLink": true,
            "type": "PRIMARY"
          },
          {
            "id": 22,
            "href": "https://docs.strapi.io",
            "label": "How It Works",
            "isExternal": true,
            "isButtonLink": true,
            "type": "SECONDARY"
          }
        ],
        "image": {
          "id": 6,
          "documentId": "pxuhf5ukwzafkmb8ue8biagy",
          "alternativeText": null,
          "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/tables_921e2e7dac.avif"
        }
      },
      {
        "__component": "blocks.section-heading",
        "id": 2,
        "subHeading": "Dolor sit amet consectutar",
        "heading": "Build & Launch without problems",
        "anchorLink": "section-1"
      },
      {
        "__component": "blocks.card-grid",
        "id": 2,
        "cards": [
          {
            "id": 7,
            "heading": "Lorem ipsum dolor sit amet consectutar",
            "text": "Fusce quam tellus, placerat eu metus ut, viverra aliquet purus. Suspendisse potenti. Nulla non nibh feugiat."
          },
          {
            "id": 8,
            "heading": "Ut congue nec leo eget aliquam",
            "text": "Ut tempus tellus ac nisi vestibulum tempus. Nunc tincidunt lectus libero, ac ultricies augue elementum at."
          },
          {
            "id": 9,
            "heading": "Proin fringilla eleifend justo pellentesque",
            "text": "Donec ut ligula nunc. Mauris blandit vel est et facilisis. Integer sapien felis, aliquet at posuere et, porttitor quis ligula."
          },
          {
            "id": 10,
            "heading": "Morbi sagittis ligula sit amet elit maximus",
            "text": "Duis ut facilisis orci. Morbi lacinia nunc a augue eleifend, sed placerat ex faucibus. Duis ante arcu, pretium ac luctus vulputate."
          }
        ]
      },
      {
        "__component": "blocks.content-with-image",
        "id": 3,
        "reversed": false,
        "heading": "Morbi scelerisque nulla et lectus dignissim eleifend nulla eu nulla a metus",
        "content": "Quisque id sagittis turpis. Nulla sollicitudin rutrum eros eu dictum. Integer sit amet erat sit amet lectus lacinia mattis. Donec est tortor, fermentum at urna a, accumsan suscipit sem.\n\n",
        "link": null,
        "image": {
          "id": 7,
          "documentId": "m6k376b2oa58vg2dnu5lsv0i",
          "alternativeText": null,
          "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/forest_562bafce29.avif"
        }
      },
      {
        "__component": "blocks.content-with-image",
        "id": 4,
        "reversed": true,
        "heading": "Morbi scelerisque nulla et lectus dignissim eleifend nulla eu nulla a metus",
        "content": "Quisque id sagittis turpis. Nulla sollicitudin rutrum eros eu dictum. Integer sit amet erat sit amet lectus lacinia mattis. Donec est tortor, fermentum at urna a, accumsan suscipit sem.",
        "link": {
          "id": 20,
          "href": "https://strapi.io",
          "label": "Try Strapi",
          "isExternal": true,
          "isButtonLink": true,
          "type": "PRIMARY"
        },
        "image": {
          "id": 7,
          "documentId": "m6k376b2oa58vg2dnu5lsv0i",
          "alternativeText": null,
          "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/forest_562bafce29.avif"
        }
      },
      {
        "__component": "blocks.markdown",
        "id": 2,
        "content": "## Introduction\nFreelancing as a developer is an exciting path that offers independence and financial growth. However, getting started can feel overwhelming without proper guidance. By focusing on key areas like skill development, networking, and client acquisition, you can establish a successful freelancing career.\n\n## Building a Strong Portfolio\nYour portfolio is your strongest asset as a freelancer. Instead of listing skills, showcase projects that demonstrate your capabilities. Consider building personal projects, contributing to open source, or offering pro bono work to gain experience. A well-presented portfolio builds trust with potential clients."
      },
      {
        "__component": "blocks.person-card",
        "id": 2,
        "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque et placerat metus. Morbi aliquet felis sit amet erat finibus, ac condimentum ligula ornare.",
        "personName": "Alice Bradley",
        "personJob": "Backend Developer",
        "image": {
          "id": 8,
          "documentId": "uka7pcf3dw7yczakvaj6dv3o",
          "alternativeText": null,
          "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/image_of_women_fa698d5653.avif"
        }
      },
      {
        "__component": "blocks.faqs",
        "id": 2,
        "faq": [
          {
            "id": 11,
            "heading": "How many cats does Paul have?",
            "text": "He has two cats."
          },
          {
            "id": 12,
            "heading": "What are their names?",
            "text": "Olive and Gracie."
          }
        ]
      },
      {
        "__component": "blocks.featured-articles",
        "id": 2,
        "articles": []
      },
      {
        "__component": "blocks.newsletter",
        "id": 2,
        "heading": "Stay updated with our team",
        "text": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.\n\n",
        "placeholder": "example@email.com",
        "label": "Submit",
        "formId": null
      }
    ]
  },
  "meta": {}
}
```

**Block Types Found:**

- `blocks.hero` - heading, text, links[], image
- `blocks.section-heading` - subHeading, heading, anchorLink
- `blocks.card-grid` - cards[] with heading and text
- `blocks.content-with-image` - heading, content, link, image, reversed (boolean)
- `blocks.markdown` - content (markdown string)
- `blocks.person-card` - text, personName, personJob, image
- `blocks.faqs` - faq[] with heading and text
- `blocks.featured-articles` - articles[]
- `blocks.newsletter` - heading, text, placeholder, label, formId




### 3. Article (Collection Type )

**GET** `https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/articles`

```json
{
  "data": [
    {
      "id": 12,
      "documentId": "be9fsxd1j04vgqdsmgq6edsp",
      "title": "How to Improve Your Productivity as a Developer",
      "description": "Developers often struggle with productivity due to distractions, inefficient workflows, and burnout.",
      "slug": "how-to-improve-your-productivity-as-a-developer",
      "content": "# Introduction\n\nDevelopers often struggle with productivity...",
      "createdAt": "2025-08-03T01:13:44.951Z",
      "updatedAt": "2025-08-03T01:18:30.484Z",
      "publishedAt": "2025-08-03T01:18:30.491Z",
      "featuredImage": {
        "id": 7,
        "documentId": "abc123",
        "alternativeText": null,
        "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/forest_562bafce29.avif"
      },
      "author": {
        "id": 2,
        "documentId": "k4510nw2eyzzz0udzxkq0vpm",
        "fullName": "Jacke Brown",
        "bio": "I am a fullstack developer",
        "image": {
          "id": 8,
          "documentId": "xyz789",
          "alternativeText": null,
          "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/image_of_women_fa698d5653.avif"
        }
      },
      "contentTags": [
        {
          "id": 1,
          "documentId": "ynz9y1i6fgnony4pevrta8vw",
          "title": "Tech",
          "description": "Articles about tech"
        }
      ],
      "relatedArticles": [
        {
          "id": 11,
          "documentId": "def456",
          "title": "The Benefits of Headless CMS for Modern Websites",
          "slug": "benefits-of-headless-cms"
        },
        {
          "id": 10,
          "documentId": "ghi789",
          "title": "The Challenges of Learning to Code as a Self-Taught Developer",
          "slug": "challenges-self-taught-developer"
        }
      ]
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 1,
      "total": 1
    }
  }
}
```

### 4. Articles with Pagination (Collection Type)
**GET** `https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/articles?pagination[page]=1&pagination[pageSize]=3`

Example showing how to fetch paginated articles (3 per page):

```json
{
  "data": [
    {
      "id": 12,
      "documentId": "be9fsxd1j04vgqdsmgq6edsp",
      "title": "How to Improve Your Productivity as a Developer",
      "description": "Developers often struggle with productivity due to distractions, inefficient workflows, and burnout.",
      "slug": "how-to-improve-your-productivity-as-a-developer",
      "content": "# Introduction\n\nDevelopers often struggle with productivity...",
      "createdAt": "2025-08-03T01:13:44.951Z",
      "updatedAt": "2025-08-03T01:18:30.484Z",
      "publishedAt": "2025-08-03T01:18:30.491Z",
      "featuredImage": {
        "id": 7,
        "documentId": "abc123",
        "alternativeText": null,
        "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/forest_562bafce29.avif"
      },
      "author": {
        "id": 2,
        "documentId": "k4510nw2eyzzz0udzxkq0vpm",
        "fullName": "Jacke Brown",
        "bio": "I am a fullstack developer",
        "image": {
          "id": 8,
          "documentId": "xyz789",
          "alternativeText": null,
          "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/image_of_women_fa698d5653.avif"
        }
      },
      "contentTags": [
        {
          "id": 1,
          "documentId": "ynz9y1i6fgnony4pevrta8vw",
          "title": "Tech",
          "description": "Articles about tech"
        }
      ],
      "relatedArticles": []
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 3,
      "pageCount": 2,
      "total": 6
    }
  }
}
```

**Pagination Parameters:**
- `pagination[page]` - Page number (starts at 1)
- `pagination[pageSize]` - Number of items per page
- Response includes `meta.pagination` with:
  - `page` - Current page
  - `pageSize` - Items per page
  - `pageCount` - Total number of pages
  - `total` - Total number of items

### 5. Single Page by Slug (Collection Type)
**GET** `https://inviting-cheese-ce66d3b9e0.strapiapp.com/api/pages?filters[slug][$eq]=about`

Fetch a specific page by slug:

```json
{
  "data": [
    {
      "id": 4,
      "documentId": "o9p6ce436bg3nj9ai0314hbl",
      "title": "About Page",
      "description": "This is our about page.",
      "slug": "about",
      "createdAt": "2025-04-12T04:31:18.470Z",
      "updatedAt": "2025-08-03T01:19:34.784Z",
      "publishedAt": "2025-08-03T01:19:34.791Z",
      "blocks": [
        {
          "__component": "blocks.person-card",
          "id": 4,
          "text": "Hello, you wonderful person.",
          "personName": "Jackie Brown",
          "personJob": "Backend Developer",
          "image": {
            "id": 8,
            "documentId": "uka7pcf3dw7yczakvaj6dv3o",
            "alternativeText": null,
            "url": "https://inviting-cheese-ce66d3b9e0.media.strapiapp.com/image_of_women_fa698d5653.avif"
          }
        }
      ]
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 1,
      "total": 1
    }
  }
}
```

**Note:** Pages use the same block system as the landing page. Use the same `BlockRenderer` component to render page blocks.

## Implementation Requirements

### 1. Setup & Dependencies

```bash
npm install @strapi/client @tanstack/react-query
```

### 2. API Layer (`lib/strapi.ts`)

Must use Strapi Client Library: https://github.com/strapi/client

Create Strapi client and API functions:

```typescript
import { strapi } from '@strapi/client';

const client = strapi({
  baseURL: "https://inviting-cheese-ce66d3b9e0.strapiapp.com",
});

// Get global settings
export async function getGlobal() {
  const response = await client.single("global").find();
  return response.data;
}

// Get landing page
export async function getLandingPage() {
  const response = await client.single("landing-page").find();
  return response.data;
}

// Get articles with search and pagination
export async function getArticles(params?: {
  search?: string;
  page?: number;
  pageSize?: number;
}) {
  const { search, page = 1, pageSize = 6 } = params || {};

  const response = await client.collection("articles").find({
    ...(search && {
      filters: {
        $or: [
          { title: { $containsi: search } },
          { description: { $containsi: search } },
        ],
      },
    }),
    pagination: { page, pageSize },
  });

  return {
    articles: response.data,
    pagination: response.meta?.pagination,
  };
}

// Get single article by slug
export async function getArticleBySlug(slug: string) {
  const response = await client.collection("articles").find({
    filters: { slug: { $eq: slug } },
  });
  return response.data?.[0] || null;
}

// Get single page by slug
export async function getPageBySlug(slug: string) {
  const response = await client.collection("pages").find({
    filters: { slug: { $eq: slug } },
  });
  return response.data?.[0] || null;
}
```

**Strapi v5 Filter Operators:**

- `$eq` - Equals
- `$ne` - Not equals
- `$containsi` - Contains (case insensitive)
- `$or` - Logical OR for multiple conditions

### 3. React Query Hooks (`hooks/`)

Wrap API functions with TanStack Query:

- `useGlobal()` - Global settings
- `useLandingPage()` - Landing page
- `useArticles(search, page)` - Articles with search/pagination
- `useArticle(slug)` - Single article by slug
- `usePage(slug)` - Single page by slug

### 4. TypeScript Types (`types/strapi.ts`)

**CRITICAL:** Use the exact API response structures shown above to create your TypeScript interfaces and Routes.

Key types to create:

- `Global`, `Banner`, `Header`, `Footer`, `Link`, `Image`
- `Author`, `Tag`, `Article`, `Page`
- `LandingPage`, `Block` (union type for all block types)
- Pagination metadata types

### 5. Pages & Components

**Landing Page (`/`)**

- Fetch landing page data
- Create `BlockRenderer` component that maps `block.__component` to React components
- Dynamically render blocks array

**Articles Listing (`/articles`)**

- Search with debouncing (300ms)
- Pagination with URL query params (`?search=query&page=2`)
- Responsive grid (3 cols desktop, 2 tablet, 1 mobile)
- Loading skeletons and empty states

**Single Article (`/articles/:slug`)**

- Fetch by slug, show 404 if not found
- Display: featured image, title, description, author (with bio/image), tags
- Render markdown content
- Related articles section

**Dynamic Pages (`/:slug`)**

- Use `usePage(slug)` hook to fetch page by slug
- Render page with blocks using the same `BlockRenderer` component
- Show 404 if page not found
- Examples: `/about`, `/test`, or any custom page slug

**Global Layout**

- Header with navigation (from `global.header`)
- Footer (from `global.footer`)
- Dismissible banner (from `global.banner`)
- Mobile responsive navigation

**Block Components**
Create individual React components for each `__component` type discovered in the blocks array.

### 6. Development Standards

- TypeScript strict mode
- Mobile-first responsive design
- Semantic HTML + ARIA labels for accessibility
- Error boundaries + 404 handling
- Loading skeletons (not spinners)
- Client-side routing with React Router

## Project Structure

```
src/
├── lib/
│   └── strapi.ts          # API utility functions
├── hooks/
│   └── useStrapi.ts       # React Query hooks
├── types/
│   └── strapi.ts          # TypeScript interfaces (from actual API responses)
├── components/
│   ├── blocks/            # Block components for dynamic zones
│   ├── BlockRenderer.tsx  # Maps __component to components
│   ├── ArticleCard.tsx    # Reusable article card
│   └── Layout.tsx         # Global header, footer, banner
└── pages/
    ├── LandingPage.tsx    # Home route
    ├── ArticlesPage.tsx   # Articles listing with search/pagination
    └── ArticlePage.tsx    # Single article view
```

## Key Implementation Notes

**Data Access Patterns:**

```typescript
// Direct field access (Strapi v5)
article.title;
article.featuredImage.url;
article.author.fullName;
article.author.image.url;
article.contentTags.map((tag) => tag.title);
article.relatedArticles[0].title;

// Global data
global.banner.isVisible;
global.header.navItems;
global.footer.socialLinks;
```

**Dynamic Block Rendering:**

```typescript
const blockComponents = {
  "blocks.hero": HeroBlock,
  "blocks.section-heading": SectionHeadingBlock,
  "blocks.card-grid": CardGridBlock,
  // ... map each __component to its React component
};

blocks.map((block) => {
  const Component = blockComponents[block.__component];
  return <Component key={block.id} {...block} />;
});
```

## Specifications & Acceptance Criteria

### Feature 1: Global Layout
**Requirements:**
- Fetch global data using `useGlobal()` hook
- Render header with logo, navigation items, and CTA button
- Render footer with logo, navigation items, and social links
- Implement dismissible banner (save state to localStorage)
- Mobile hamburger menu with smooth transitions

**Acceptance Criteria:**
- ✅ Navigation renders all links from API
- ✅ Logo image displays with correct alt text
- ✅ Banner can be dismissed and stays hidden after refresh
- ✅ Mobile menu opens/closes smoothly on tablet and mobile
- ✅ CTA button has correct styling based on type (PRIMARY/SECONDARY)

### Feature 2: Landing Page with Dynamic Blocks
**Requirements:**
- Fetch landing page data using `useLandingPage()` hook
- Create `BlockRenderer` that maps `__component` to React components
- Implement all 9 block types with proper styling
- Handle loading and error states

**Acceptance Criteria:**
- ✅ All blocks render in correct order
- ✅ Each block type displays data correctly from API
- ✅ Images have proper alt text and lazy loading
- ✅ Links work and external links open in new tab
- ✅ Responsive design works on all screen sizes

### Feature 3: Articles Listing Page
**Requirements:**
- Fetch articles using `useArticles(search, page)` hook
- Implement search with 300ms debounce
- URL query params for search and page state
- Pagination controls (prev/next, page numbers)
- Responsive grid layout

**Acceptance Criteria:**
- ✅ Articles display in 3/2/1 column grid (desktop/tablet/mobile)
- ✅ Search filters articles by title and description
- ✅ Pagination updates URL and maintains search state
- ✅ Loading shows skeleton cards (not spinner)
- ✅ Empty state shows when no articles found

### Feature 4: Single Article Page
**Requirements:**
- Fetch article by slug using `useArticle(slug)` hook
- Display featured image, title, description, author, tags
- Render markdown content
- Render article blocks using `BlockRenderer`
- Display related articles in grid
- Show 404 page if article not found

**Acceptance Criteria:**
- ✅ Article content renders from markdown correctly
- ✅ Author info displays with image and bio
- ✅ Tags are clickable and styled as pills
- ✅ Related articles show in card grid
- ✅ 404 page appears for invalid slugs

### Feature 5: Dynamic Pages
**Requirements:**
- Fetch page by slug using `usePage(slug)` hook
- Reuse `BlockRenderer` for page blocks
- Show 404 if page not found
- Match routes from global navigation

**Acceptance Criteria:**
- ✅ Pages render blocks correctly
- ✅ Navigation links work for all pages
- ✅ 404 shows for invalid slugs
- ✅ Page title and description display

## Implementation TODO Checklist

### Phase 1: Foundation (Setup & Types)
- [ ] **Task 1.1**: Install dependencies (@strapi/client, @tanstack/react-query)
- [ ] **Task 1.2**: Create TypeScript interfaces in `types/strapi.ts` based on API responses
  - Global, Banner, Header, Footer, Link, Image types
  - Article, Author, Tag types
  - Page and LandingPage types
  - Block union type for all 9 block types
  - Pagination metadata types
- [ ] **Task 1.3**: Verify types match exact API field names (NO assumptions!)

### Phase 2: API Layer
- [ ] **Task 2.1**: Create `lib/strapi.ts` with Strapi client
- [ ] **Task 2.2**: Implement `getGlobal()` function
- [ ] **Task 2.3**: Implement `getLandingPage()` function
- [ ] **Task 2.4**: Implement `getArticles(params)` with search and pagination
- [ ] **Task 2.5**: Implement `getArticleBySlug(slug)` function
- [ ] **Task 2.6**: Implement `getPageBySlug(slug)` function

### Phase 3: React Query Hooks
- [ ] **Task 3.1**: Create `hooks/useStrapi.ts` file
- [ ] **Task 3.2**: Implement `useGlobal()` hook
- [ ] **Task 3.3**: Implement `useLandingPage()` hook
- [ ] **Task 3.4**: Implement `useArticles(search, page)` hook
- [ ] **Task 3.5**: Implement `useArticle(slug)` hook
- [ ] **Task 3.6**: Implement `usePage(slug)` hook
- [ ] **Task 3.7**: Setup QueryClientProvider in App

### Phase 4: Global Layout Components
- [ ] **Task 4.1**: Create `components/Layout.tsx` wrapper
- [ ] **Task 4.2**: Create `components/Header.tsx`
  - Render logo with image
  - Render navigation items
  - Render CTA button
  - Implement mobile hamburger menu
- [ ] **Task 4.3**: Create `components/Footer.tsx`
  - Render footer logo
  - Render footer navigation
  - Render social links with icons
- [ ] **Task 4.4**: Create dismissible banner component
  - Show/hide based on localStorage
  - Close button functionality

### Phase 5: Block Components (Dynamic Zones)
- [ ] **Task 5.1**: Create `components/BlockRenderer.tsx` with component mapping
- [ ] **Task 5.2**: Create `components/blocks/HeroBlock.tsx`
  - Display heading, text, links, and background image
- [ ] **Task 5.3**: Create `components/blocks/SectionHeadingBlock.tsx`
  - Display subHeading, heading, and anchor link
- [ ] **Task 5.4**: Create `components/blocks/CardGridBlock.tsx`
  - Render cards in responsive grid
- [ ] **Task 5.5**: Create `components/blocks/ContentWithImageBlock.tsx`
  - Support reversed layout
  - Render link button if present
- [ ] **Task 5.6**: Create `components/blocks/MarkdownBlock.tsx`
  - Use markdown renderer library
- [ ] **Task 5.7**: Create `components/blocks/PersonCardBlock.tsx`
  - Display person image, name, job, and text
- [ ] **Task 5.8**: Create `components/blocks/FaqsBlock.tsx`
  - Implement accordion UI for FAQ items
- [ ] **Task 5.9**: Create `components/blocks/NewsletterBlock.tsx`
  - Form with email input
- [ ] **Task 5.10**: Create `components/blocks/FeaturedArticlesBlock.tsx`
  - Display articles if provided

### Phase 6: Page Components
- [ ] **Task 6.1**: Create `pages/LandingPage.tsx`
  - Fetch landing page data
  - Render title and description
  - Render blocks using BlockRenderer
- [ ] **Task 6.2**: Create `components/ArticleCard.tsx`
  - Display featured image, title, description
  - Show author name and tags
  - Link to article detail page
- [ ] **Task 6.3**: Create `pages/ArticlesPage.tsx`
  - Implement article grid
  - Add search input with debouncing
  - Add pagination controls
  - Show loading skeletons
  - Show empty state when no results
- [ ] **Task 6.4**: Create `pages/ArticlePage.tsx`
  - Display article header (image, title, description)
  - Render markdown content
  - Render article blocks
  - Display author card
  - Show related articles
  - Handle 404 for invalid slug
- [ ] **Task 6.5**: Create `pages/DynamicPage.tsx`
  - Fetch page by slug
  - Render blocks using BlockRenderer
  - Handle 404 for invalid slug
- [ ] **Task 6.6**: Create `pages/NotFoundPage.tsx`
  - 404 error page with helpful message

### Phase 7: Routing & Integration
- [ ] **Task 7.1**: Setup React Router in App.tsx
  - Route: `/` → LandingPage
  - Route: `/articles` → ArticlesPage
  - Route: `/articles/:slug` → ArticlePage
  - Route: `/:slug` → DynamicPage (for pages like /about)
  - Route: `*` → NotFoundPage
- [ ] **Task 7.2**: Generate routes dynamically from `global.header.navItems`
- [ ] **Task 7.3**: Wrap all routes with Layout component

### Phase 8: Polish & Testing
- [ ] **Task 8.1**: Add error boundaries to each page
- [ ] **Task 8.2**: Implement loading states for all data fetching
- [ ] **Task 8.3**: Add aria-labels for accessibility
- [ ] **Task 8.4**: Test all pages with real API data
- [ ] **Task 8.5**: Test responsive design on mobile, tablet, desktop
- [ ] **Task 8.6**: Test navigation between pages
- [ ] **Task 8.7**: Test search and pagination functionality
- [ ] **Task 8.8**: Verify all images have alt text

## Verification Checkpoints

After completing each phase, verify:

**Phase 1-3 Checkpoint:**
- [ ] API calls return data successfully
- [ ] TypeScript types match API responses exactly
- [ ] React Query hooks work without errors

**Phase 4 Checkpoint:**
- [ ] Header and footer display correctly
- [ ] Navigation links work
- [ ] Banner can be dismissed
- [ ] Mobile menu functions properly

**Phase 5 Checkpoint:**
- [ ] BlockRenderer maps all block types
- [ ] Each block component renders sample data
- [ ] No TypeScript errors

**Phase 6-7 Checkpoint:**
- [ ] Landing page renders all blocks
- [ ] Articles page shows grid and pagination
- [ ] Article detail page displays correctly
- [ ] Dynamic pages work for /about route
- [ ] 404 page shows for invalid URLs

**Final Verification:**
- [ ] All pages load and display real data
- [ ] Navigation works across all pages
- [ ] Search finds articles correctly
- [ ] Pagination maintains state
- [ ] Mobile responsive on all pages
- [ ] No console errors
- [ ] All images load with alt text

## Important Reminders

1. **Field Names**: Use EXACT field names from API responses
2. **Strapi v5**: Direct field access (NO `.attributes` nesting)
3. **No Populate**: Relations auto-populated by backend middleware
4. **Filter Syntax**: Use Strapi v5 operators (`$eq`, `$containsi`, `$or`)
5. **Loading States**: Use skeleton loaders, NOT spinners
6. **Mobile First**: Design for mobile, then scale up
7. **Accessibility**: Add alt text, ARIA labels, semantic HTML

## Start Building

Begin with Phase 1 and work through each task sequentially. After completing each phase, run the verification checkpoint before moving to the next phase.
