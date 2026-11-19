# SEO Bank MCP (بنك السيو)

A free **MCP server** that lets AI agents (Claude, ChatGPT, Cursor, and any MCP client) search **[SEO Bank](https://seoquestionsbank.com/)**, an Arabic SEO knowledge base, read the full step-by-step fix for each problem, and **audit any public page**, get the fix for each issue, and re-check after deploying.

- **Server URL:** `https://seoquestionsbank.com/mcp`
- **Transport:** Streamable HTTP (stateless, JSON)
- **Auth:** none. Read-only: it reads public pages and the bank; it never writes to your site.
- **Language:** Arabic content, search works with Arabic or English words.
- **Arabic setup guide:** https://seoquestionsbank.com/mcp-server/

> This repository only documents the hosted server. The server itself runs on seoquestionsbank.com; there is nothing to install.

## Tools (8)

### Fix a live page

| Tool | What it does |
| --- | --- |
| `audit_page` | Fetch one public page like Googlebot (server HTML, robots.txt, redirects) and list its SEO issues by severity, with a score /100, page facts (title, description, H1, canonical, noindex, words, images without alt, schema) and a guide link per issue. |
| `get_fix` | Everything needed to fix one issue id: why it matters, the short fix, the free tool that checks it, and the full answer from the bank as Markdown. |
| `recheck_page` | Audit the live page again after you deploy and report which issue ids are fixed, which remain, and any new ones. |

### Search the bank

| Tool | What it does |
| --- | --- |
| `search_seo_questions` | Keyword search over 88+ SEO problems (on-page, off-page, technical), ranked by relevance. Optional `category` filter, `limit` (up to 20) and `offset` for paging; returns `total` and `nextOffset`. |
| `get_seo_question` | Get the full answer for one question as Markdown: symptoms, cause, tools, fix steps, WordPress steps and sources. Pass an id or the page URL. |
| `list_seo_categories` | List the categories (`onpage`, `offpage`, `technical`) with what they cover and how many questions each has. |
| `get_seo_category` | Details for one category: intro, question count, main topics and the latest questions. |
| `list_seo_questions` | Browse questions without a keyword, newest first. Filter by `category`, page with `limit` and `offset`. |

The older names `search_seo_bank` and `get_seo_answer` still work.

Rate limits: 6 page audits per minute per client, 30 requests per minute for everything else.

## Connect

**Claude Code**

```bash
claude mcp add --transport http seo-bank https://seoquestionsbank.com/mcp
```

**Claude Desktop / claude.ai:** Settings → Connectors → Add custom connector → paste `https://seoquestionsbank.com/mcp`.

**Cursor** (`.cursor/mcp.json`):

```json
{ "mcpServers": { "seo-bank": { "url": "https://seoquestionsbank.com/mcp" } } }
```

**VS Code / GitHub Copilot** (`.vscode/mcp.json`):

```json
{ "servers": { "seo-bank": { "type": "http", "url": "https://seoquestionsbank.com/mcp" } } }
```

More clients (Windsurf, Gemini CLI, Codex, ChatGPT): https://seoquestionsbank.com/mcp-server/

## Example prompts

- "Use seo-bank to audit my homepage, fix the critical and error issues in the code, deploy, then recheck_page."
- "Why are my pages *Crawled – currently not indexed*? Use seo-bank and cite the source."
- "الصفحات مش بتتفهرس في جوجل، إيه الحل؟"

## Crawler

Page audits are sent with the user agent `SEOBankBot/1.0` (https://seoquestionsbank.com/bot/). It only visits a page when someone asks for an audit.

## More from SEO Bank

- [40 free SEO tools](https://seoquestionsbank.com/free-tools/) (Arabic keyword variants, Arabic pixel-width title checker, AI readiness checker, robots.txt tester, schema generator, and more)
- [Chrome extension](https://chromewebstore.google.com/detail/lmlkimlingpbabemloidjllfeokglafc) for one-click on-page SEO audits
- [`llms.txt`](https://seoquestionsbank.com/llms.txt) and [`llms-full.txt`](https://seoquestionsbank.com/llms-full.txt)

---

## بالعربي

**بنك السيو** مرجع عربي مجاني لحل مشاكل السيو خطوة بخطوة. سيرفر الـ MCP ده بيخلي أدوات الذكاء الاصطناعي تدوّر في البنك وتقرا الحل كامل، وكمان تفحص أي صفحة وتاخد الحل لكل مشكلة وتعيد الفحص بعد التصليح. مجاني، ومن غير تسجيل دخول، وللقراءة بس. الشرح بالعربي: https://seoquestionsbank.com/mcp-server/

إعداد [مهندس محمد عيد](https://seoquestionsbank.com/author/mohamed-eid/).
