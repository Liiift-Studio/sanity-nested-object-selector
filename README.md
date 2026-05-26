# sanity-nested-object-selector

[![npm version](https://img.shields.io/npm/v/@liiift-studio/sanity-nested-object-selector.svg)](https://www.npmjs.com/package/@liiift-studio/sanity-nested-object-selector)

Sanity Studio searchable checkbox selector for items nested within another document type. Builds GROQ queries dynamically and supports full-text search, toggle-all, and selection count feedback.

## Install

```bash
npm install @liiift-studio/sanity-nested-object-selector
```

## Usage

Use `NestedObjectArraySelector` as a custom `input` component on an array field:

```typescript
import { NestedObjectArraySelector } from '@liiift-studio/sanity-nested-object-selector'

export const mySchema = defineType({
	name: 'collection',
	type: 'document',
	fields: [
		defineField({
			name: 'products',
			title: 'Products',
			type: 'array',
			of: [{ type: 'string' }],
			components: {
				input: NestedObjectArraySelector,
			},
			options: {
				sourceType: 'category',        // Document type that contains the nested array
				nestedField: 'products',       // Array field name within sourceType
				titleField: 'name',            // Field to display for each item
				valueField: '_id',             // Field to use as the stored value
				filter: 'status == "active"',  // Optional GROQ filter
				sortBy: 'name asc',            // Optional GROQ sort
				searchPlaceholder: 'Search products...',
				emptyMessage: 'No products found',
			},
		}),
	],
})
```

## Features

- Full-text search across all items
- Checkbox selection with toggle-all
- Selected count indicator
- Dynamic GROQ query generation
- Automatic deduplication by value field

## Peer Dependencies

| Package | Version |
|---|---|
| `@sanity/ui` | `>=3` |
| `react` | `>=18` |
| `sanity` | `>=3` |
