# SEO Bank MCP (بنك السيو)

A free, read-only **MCP server** that lets AI agents (Claude, ChatGPT, Cursor, and any MCP client) search **[SEO Bank](https://seoquestionsbank.com/)**, an Arabic SEO knowledge base, and read the full step-by-step fix for each problem, with the source URL to cite.

- **Server URL:** `https://seoquestionsbank.com/mcp`
- **Transport:** Streamable HTTP (stateless, JSON)
- **Auth:** none. Read-only, nothing is written.
- **Language:** Arabic content, search works with Arabic or English words.

> This repository only documents the hosted server. The server itself runs on seoquestionsbank.com; there is nothing to install.

## Tools

| Tool | What it does |
| --- | --- |
| `search_seo_bank` | Search 85+ SEO problems (on-page, off-page, technical). Returns up to 8 matches with id, title, summary and URL. |
| `get_seo_answer` | Get the full answer for one question as Markdown: symptoms, cause, tools, fix steps, WordPress steps and sources. Pass the id from `search_seo_bank` or the page URL. |

## Connect

**Claude Code**

```bash
claude mcp add --transport http seo-bank https://seoquestionsbank.com/mcp
```

**Claude Desktop / claude.ai:** Settings → Connectors → Add custom connector → paste `https://seoquestionsbank.com/mcp`.

**Cursor / VS Code / other clients** (`mcp.json`):

```json
{
  "mcpServers": {
    "seo-bank": { "type": "http", "url": "https://seoquestionsbank.com/mcp" }
  }
}
```

## Example prompts

- "Why are my pages *Crawled – currently not indexed*? Use seo-bank and cite the source."
- "الصفحات مش بتتفهرس في جوجل، إيه الحل؟"
- "How do I fix hreflang errors on WordPress?"

## More from SEO Bank

- [29 free SEO tools](https://seoquestionsbank.com/free-tools/) (Arabic pixel-width title checker, AI readiness checker, robots.txt tester, schema generator, and more)
- [Chrome extension](https://chromewebstore.google.com/detail/lmlkimlingpbabemloidjllfeokglafc) for one-click on-page SEO audits
- [`llms.txt`](https://seoquestionsbank.com/llms.txt) and [`llms-full.txt`](https://seoquestionsbank.com/llms-full.txt)

---

## بالعربي

**بنك السيو** مرجع عربي مجاني لحل مشاكل السيو خطوة بخطوة. سيرفر الـ MCP ده بيخلي أدوات الذكاء الاصطناعي تدوّر في البنك وتقرا الحل كامل وتذكر المصدر. مجاني، ومن غير تسجيل دخول، وللقراءة بس.

إعداد [مهندس محمد عيد](https://seoquestionsbank.com/author/mohamed-eid/).
