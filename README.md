# astro-better-cards

Clickable card components for Astro docs sites. Three variants: `full` (large card with optional image/icon), `compact` (nav row with optional label), and `quickstart` (small icon + title, with coming-soon support).

## Install

```
npm install astro-better-cards
```

## Usage

```mdx
import Card from 'astro-better-cards/Card.astro';
```

### full (default)

Large bordered card. Good for section index pages.

```mdx
<Card href="/docs/section" title="Section Title" description="A short description." />
```

With an icon:

```mdx
<Card href="/docs/section" title="Section Title" icon="/img/icon.svg" darkIcon="/img/icon-dark.svg" />
```

With a card image (displayed above the content):

```mdx
<Card href="/docs/section" title="Section Title" cardImage="/img/banner.png" />
```

### compact

Small nav row, often used for prev/next links. The `label` prop renders a short badge (e.g. an arrow). `labelFirst` controls which side the label appears on.

```mdx
<Card variant="compact" href="/docs/next-page" title="Next Page" label="->" labelFirst={true} />
<Card variant="compact" href="/docs/prev-page" title="Previous Page" label="<-" labelFirst={false} />
```

### quickstart

Small icon + title card for quickstart grids. Supports a `comingSoon` state that greys out the card.

```mdx
<Card variant="quickstart" href="/docs/quickstart/react" title="React" icon="/img/react.svg" />
<Card variant="quickstart" href="" title="Vue" icon="/img/vue.svg" comingSoon={true} />
```

## Props

| Prop | Variants | Type | Default | Description |
|------|----------|------|---------|-------------|
| `href` | all | `string` | — | Link destination. |
| `title` | all | `string` | — | Card title. Rendered with `set:html` so HTML entities and inline markup work. |
| `variant` | all | `'full' \| 'compact' \| 'quickstart'` | `'full'` | Which card style to render. |
| `description` | `full` | `string` | — | Optional subtitle below the title. |
| `icon` | `full`, `quickstart` | `string` | — | Icon image URL. Hidden in dark mode when `darkIcon` is also set. |
| `darkIcon` | `full` | `string` | — | Dark-mode icon image URL. |
| `cardImage` | `full` | `string` | — | Banner image displayed above the card content. |
| `label` | `compact` | `string` | — | Short badge text (e.g. `"->"`, `"<-"`, a step number). |
| `labelFirst` | `compact` | `boolean` | `false` | When `true`, the label appears after the title (right-aligned). |
| `comingSoon` | `quickstart` | `boolean` | `false` | Greys out the card and appends `* Coming Soon` to the title. |

## Styling

Cards use Tailwind CSS utility classes and respond to dark mode via the `dark:` variant. No Tailwind integration is required in your project -- classes are inlined in the component.
