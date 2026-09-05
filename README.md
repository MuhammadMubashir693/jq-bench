# JQ Bench — JSON Query Workbench

A lightweight, browser-based JSON query and editing workbench. Load JSON data, explore its structure, search and filter records, sort results, select columns, modify data, and export results — all without a backend.

## Features

### Load JSON

- Paste JSON directly into the application.
- Upload `.json` files using the file picker or drag and drop. Each opened file gets its own tab.
- Supports JSON arrays and objects.
- Specify an optional root path for nested arrays, such as `data.items` or `response.results`.

### Browse JSON

The **Browse** tab provides a tree view of loaded JSON.

- Expand and collapse objects and arrays.
- See object and array sizes.
- Copy JSON paths from the tree.

### Search and Query

The **Query** tab provides tools for working with loaded data.

#### Global Search

Search across all fields using a case-insensitive text search.

#### Filters

Multiple conditions can be combined using:

- `AND`
- `OR`
- `NOT`

Supported operators include:

- `=`
- `!=`
- `contains`
- `startsWith`
- `endsWith`
- `regex`
- `>`
- `<`
- `>=`
- `<=`
- `exists`
- `is null`

`NOT` can be applied independently to conditions.

### Sorting

Add multiple sort levels and choose ascending or descending order.

### Limit and Offset

Control the returned records using offset and limit.

### Columns

Choose which fields appear in the results.

- Add columns manually.
- Detect columns automatically.
- Clear the selection to show all top-level fields.
- Extract nested values using paths.
- Work with nested arrays such as `videos[].durationSeconds`.

### Edit JSON

The **Edit JSON** tab provides a built-in JSON editor.

Available actions:

- Format JSON
- Validate JSON
- Apply changes
- Save edited JSON
- Expand the editor

### Mutate Data

The **Mutate** tab allows fields to be modified without manually editing the entire JSON document.

Supported operations include inserting/replacing fields, setting fields to `null`, and deleting fields or matching objects.

### Results

Results can be viewed as:

- Table
- Raw JSON

You can also:

- Copy results
- Download results as JSON
- Paginate results
- Change rows per page

### jq Command

JQ Bench displays an equivalent `jq` command for the current query, which can be copied to the clipboard.

## Saved Queries

Queries can be saved with a custom name and loaded later.

The application also provides:

- Export configuration
- Import configuration

Saved queries and workbench state are stored locally in the browser.

## Browser Storage

JQ Bench is a client-side application and does not require a database or backend.

The open tabs and each tab's workbench state are stored using browser `localStorage`. This includes loaded JSON, query settings, filters, sorts, columns, pagination settings, view state, tree state, column widths, and other UI state.

Storage is tied to the browser and website origin.

For example:

```text
Computer A / Firefox
        ↓
   localStorage

Computer A / Chrome
        ↓
   separate localStorage

Computer B / Firefox
        ↓
   separate localStorage
```

Data stored locally is **not automatically synchronized between browsers or devices**.

If browser/site storage is cleared, locally stored state may be removed.

## Privacy

JQ Bench processes JSON data in the browser. Its core functionality does not require a backend or database.

## Deployment

JQ Bench is a static HTML application and can be deployed to static hosting services such as Vercel.

No backend or database is required.

After deployment, `localStorage` continues to work normally. However, the deployed website has a different browser-storage origin from a local HTML file.

For example:

```text
Local HTML file
    ↓
local browser storage

https://your-project.vercel.app
    ↓
separate browser storage
```

Therefore, data saved while running the local HTML file will not automatically appear on the Vercel deployment.

Once using the Vercel URL, refreshing or reopening the application will normally preserve its `localStorage` state.

## Running Locally

JQ Bench can be opened directly in a browser:

```text
json-query-tool.html
```

It can also be served through a local web server if preferred.

## Project Structure

The application is currently implemented as a single HTML file containing:

```text
HTML
├── Interface
├── CSS
└── JavaScript
    ├── Application state
    ├── JSON loading
    ├── JSON editing
    ├── JSON mutation
    ├── Tree browser
    ├── Search
    ├── Filters
    ├── Sorting
    ├── Column projection
    ├── Pagination
    ├── Saved queries
    ├── Import/export
    ├── jq command generation
    └── Browser storage
```

## No Backend Required

JQ Bench does not require:

- Node.js
- Python
- A database
- An API server
- User accounts
- Server-side JSON processing

The core application runs entirely in the browser.

## Limitations

Because the application uses browser storage:

- Stored data is tied to a browser and origin.
- Large JSON datasets may eventually exceed browser storage limits.
- Local data is not synchronized between devices.
- Clearing browser/site storage can remove saved state.
- Saved queries are local unless their configuration is exported.

For larger datasets or multi-user synchronization, a backend and database would be required.

## License

Add your preferred license here if this project will be distributed publicly.
