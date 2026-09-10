# astro-better-cards

Components for cards and navigation in Astro documentation sites.

## Card

A single card with three display variants.

```astro
import Card from 'astro-better-cards/Card.astro';

<Card
  href="/docs/section/page"
  title="Page Title"
  description="Optional description text."
  icon="/img/icons/example.svg"
  variant="full"
/>
```

### Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `href` | `string` | required | Link destination |
| `title` | `string` | required | Card title (HTML allowed) |
| `description` | `string` | — | Subtitle text |
| `icon` | `string` | — | Icon image URL (light mode) |
| `darkIcon` | `string` | — | Icon image URL (dark mode) |
| `cardImage` | `string` | — | Hero image URL |
| `variant` | `'full' \| 'compact' \| 'quickstart'` | `'full'` | Display style |
| `comingSoon` | `boolean` | `false` | Greys out the card |
| `label` | `string` | — | Small label text (e.g. `'->'`) |
| `labelFirst` | `boolean` | `false` | Render label before title |

## ChildCards

Automatically renders cards for child pages of the current section, pulled from an Astro content collection.

```astro
import ChildCards from 'astro-better-cards/ChildCards.astro';

<!-- direct children of the current page's folder -->
<ChildCards />

<!-- grandchildren grouped by subfolder with section headers -->
<ChildCards depth={2} />

<!-- children of an explicit folder -->
<ChildCards folder="get-started/quickstarts/web" />

<!-- children from a different collection -->
<ChildCards collection="articles" />
```

Typically used via the `sectionIndex: true` front matter field (rendered automatically by the layout), or imported directly in MDX for more control.

### Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `collection` | `string` | `'docs'` | Astro content collection name |
| `folder` | `string` | current page folder | Collection-relative path (`get-started/foo`), URL-absolute path (`/docs/get-started/foo`), or relative path (`./sub`, `../other`) |
| `depth` | `1 \| 2` | `1` | `1` = direct children; `2` = grandchildren grouped under section headers |

Pages with `excludeFromNav: true` or `route: false` are excluded.

## PageNav

Renders previous/next navigation links at the bottom of a page, resolving page titles automatically from the collection.

```astro
import PageNav from 'astro-better-cards/PageNav.astro';

<PageNav
  currentId={entry.id}
  lastPage="step-1"
  nextPage="step-3"
/>
```

Or set `lastPage` / `nextPage` in front matter and let the layout render it automatically.

### Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `collection` | `string` | `'docs'` | Astro content collection name |
| `currentId` | `string` | required | The current page's `entry.id` (e.g. `get-started/start-here/step-1.mdx`) |
| `nextPage` | `string` | — | Relative href to the next page (e.g. `step-2`) or absolute (`/docs/...`) |
| `lastPage` | `string` | — | Relative href to the previous page |
