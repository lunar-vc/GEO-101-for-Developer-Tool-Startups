# GEO for Technical Marketing Content
Whereas in the past, you would write content for SEO purposes on your site: blog, tutorials, guides, etc, now that content still needs to be written but for LLM bots who scrape sites often and use the information to fuel their answers. 

Just as with SEO there are key considerations that will make the content stronger and more resonant for the LLMs, leading your site to be sited more often. These considerations should be factored int when creating new content. 

‼️ LLM bots may be able to pick up generated content. I'm of the opinion that if you don't have something to say, don't waste the website space to generate it from an LLM and put it online. 

**Write genuine content that gives value and when you do, factor in these elements**: 
### 💬 Conversational text:

LLMs like text that sounds conversational because that matches the style in which users query LLMs. Actively counter to SEO suggestions, there's no need for keyword stuffing. Avoid over the top technical jargon.

### 🔍 Depth:

When you explain things, try to also cover the subsequent further questions that a user might ask an AI.

For example, when FooBarDB writes some text explaining how " FooBarDB speeds up performance by 40%" additional questions may relate to:

- "How does FooBarDB's 40% speedup compare to other database optimization solutions?"
- "What's the implementation timeline to achieve this 40% performance improvement?"
- "Does the 40% speedup maintain consistency across different query types and workloads?"

In your text, try to cover the main topic and anticipated adjacent questions

### ⚡ Short texts:

SEO prioritized long deep texts, LLMs like shorter texts where they can get the answer quickly. This both may imply shorter content pieces and also longer pieces broken up in short digestible elements, started off with clear headings.

### 📑 Headings:

Headings should be very clear and give visibility into what's in the text (within reason); specificity is good as long as it reads normally and conversationally. Example:

- ❌ "Amazing database performance" (too vague)
- ✅ "FooBarDB speeds up performance by 40%" (just right)
- ❌ "FooBarDB increases performance by 40% compared to PostgreSQL on TPC-H benchmarks using 16-core servers" (too verbose)

### 🗂️ Clear Organization:

Content should be well-organized with clear headings, subheadings, bullet points, etc as necessary

### 📊 Quotes and Statistics:

LLMs love content with quotes and data. Once you see it in blog posts now you can't unsee it ;). There are two kinda of quotes and data you can provide, both valuable:

**🎯 Original:** this would come from your work and research. Quotes, benchmarks, studies, any stats that you develop help establish authority and credibility

**📚 Well-sourced and cited existing:** These are also useful especially when augmented by original analysis. According to Claude-"Well-cited content often ranks better because it signals quality and reliability."

### 🗓️ Up to date information:

LLM bots like up to date information and prioritize it. Two main impacts:

**⏰ Highlight timeliness:** "As of Q1, 2025", "Since November 2024," etc. Evergreen content is not impactful as timely information.

**🔄 Prioritize maintenance:** Try to keep content up date and highlight this visibly: eg. "last updated June 1st,2025"

### 🎨 Non-text elements:

Adding elements that spice up your content besides text can be positive and effective if done correctly— this make the text more interesting to read for users and provides additional assets that when translated to text for LLMs give more content to be parsed. According to Claude, "The key insight: treat LLMs like intelligent users who can read everything but are using a text-only browser". The text itself should be added using JSON-LD Structured Data. Considerations for different elements:

**🖼️ Image:** 
* Include descriptive alt text: eg. ""Bar chart showing FooBarDB at 60ms outperforming baseline (100ms) and competitors (85-90ms) in database query response times." 
* Good image alt text should be less than 125 characters.

**🎥 Video:** Include text elements to make it parsable by LLMs. These include: 
* video summary, 
* timestamped highlights (especially where key visual elements are described)
* transcript in the html (not linked out). 

**🎵 Audio:** Include text elements to make it parsable by LLMs: 
* transcript
* summary/key takeaways

**⚙️ Interactive Widget:** Add text and comments to the widgets to make them more parsable by a bot:

```html
<!-- What LLMs see -->
<button onclick="runDemo()">Run Performance Test</button>
<div id="results"></div>
						
<!-- How to help LLMs understand -->
<button onclick="runDemo()">Run Performance Test</button>
<p>This demo compares FooBarDB query speeds before and after optimization.</p>
</div>
<div id="demo-explanation">
Expected results: Original queries average 200ms, optimized queries average 120ms
</div>
```

### ❓ FAQs:

FAQs are catnip to LLMs because they offer questions phrased in the way that someone might query an LLM and have clear answers. FAQs are highly recommended at the bottom of the page.

### 🔗 Context:

LLMs love context and content that explicitly connects concepts together and highlights their relationships. Implementation include:

- Defining acronyms early on
- Defining what your company/product is and does
- Using comparison tables to explicitly highlight the relationship between the capaibitlies of your tool and the competitors
- Highlighting use cases and examples
- **Semantic Relationships:** Using transitional phrases to show how concepts connect. This is actually an interesting topic. See Claude's [take](https://claude.ai/share/700f707d-9470-4797-9e36-d82cc5c2ac27).
