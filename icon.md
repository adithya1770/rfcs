## Problem Statement

Currently, npm packages do not have a standard or official way to define an icon or logo.
As a result, package listings and tools often display only text information, or rely on
unreliable methods such as scraping README files or repository metadata.

This makes it difficult for users to visually identify and differentiate packages,
especially in large plugin or library ecosystems.

---

## Proposed Solution

This RFC proposes adding an optional `icon` field to `package.json`.
This field allows package authors to explicitly specify a URL to an image
that represents the package.

The npm registry would store this metadata and expose it in search results
and other relevant APIs.

---

## Proposal Details

- Add a new optional `icon` field to `package.json`
- The field value is a URL pointing to an image
- The npm search API should include this field in the returned `package` object
- Validation should ensure:
  - The URL is valid
  - The URL points to an image
  - Only supported image formats are allowed

Example:

```json
{
  "name": "example-package",
  "version": "1.0.0",
  "icon": "https://example.com/icon.png"
}
