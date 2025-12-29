## Problem Statement

Currently, npm packages do not have a standard or official way to define an icon or logo.
As a result, package listings and tools often display only text information, or rely on
unreliable methods such as scraping README files or repository metadata.

This makes it difficult for users to visually identify and differentiate packages,
especially in large plugin or library ecosystems.

---

## Proposed Solution

This RFC proposes adding an optional `icon` field to `package.json`
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
 
## Usefulness and Motivation

Many tools and websites that display npm packages would benefit from having
a reliable and explicit package icon.

Today, icon discovery is inconsistent and often depends on heuristics such as
parsing README files or repository pages. Introducing a dedicated icon field
gives package authors full control over how their package is visually represented.

This is especially helpful in plugin-based ecosystems, where users browse
large lists of similar packages.
 
## Safety Considerations and Drawbacks

Adding a new metadata field slightly increases package metadata size,
but does not affect existing packages or tooling.

Potential security and abuse concerns include tracking images or malicious content.
These risks can be mitigated through validation, format restrictions, size limits,
and possible proxying or caching by the registry.

Since the field is optional and backward-compatible, existing packages and clients
are not impacted.
 
## Credits

- Original issue: #8878
- Proposed by: @justjam2013

Example:

```json
{
  "name": "example-package",
  "version": "1.0.0",
  "icon": "https://example.com/icon.png"
}
