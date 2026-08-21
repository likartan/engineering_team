---
name: documentation
description: "Summarize, analyze, or explain documents — especially PDFs. Use when the user wants a summary, table of contents, key points, or plain-language explanation of a document. Trigger phrases: summarize document, explain this PDF, what does this document say, give me the key points, TL;DR of this file."
argument-hint: "Path or URL to the document you want summarized"
---

# Document Summarization

## When to Use
- User provides a PDF file path or URL and asks for a summary
- User wants the key points, main conclusions, or a TL;DR of a document
- User wants a section-by-section breakdown or table of contents
- User wants a plain-language explanation of a technical or legal document

## Procedure

### 1. Receive the Document
Accept one of the following inputs from the user:
- **Local file path** — e.g. `C:\Users\user\docs\report.pdf`
- **URL** — e.g. `https://example.com/whitepaper.pdf`

### 2. Extract the Text
- For a **URL**, fetch the page content directly.
- For a **local PDF**, ask the user to paste the text content, or if a tool can read the file, read it directly.
- If the document is very long (>20 pages), focus on: title page, abstract/executive summary, section headings, conclusions, and recommendations.

### 3. Produce the Summary
Always return the summary in this structure:

```
## Document Summary

**Title:**        <document title or filename>
**Type:**         <report | whitepaper | spec | manual | paper | contract | other>
**Length:**       <estimated pages or word count if known>
**Date/Version:** <if present in the document>

---

### TL;DR
<2-4 sentence plain-language summary of the entire document>

### Key Points
- <most important finding or claim>
- <second most important point>
- <third most important point>
(add more if the document warrants it)

### Section Breakdown
| Section | Summary |
|---------|-------- |
| <heading> | <one-line summary> |

### Conclusions & Recommendations
<What the document concludes or recommends the reader do>

### Glossary (if applicable)
| Term | Definition |
|------|------------|
| <term> | <brief definition> |
```

## Constraints
- DO NOT fabricate content not present in the document
- DO NOT reproduce large verbatim passages (copyright)
- Keep the TL;DR to 2-4 sentences maximum
- If the document cannot be read, clearly tell the user and suggest they paste the text
