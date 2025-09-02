# 🚀 Why GEO matters for your marketing website

As you work on improving your site's marketing website, factoring in how it will be read and surfaced by LLMs is key. Whereas in the past the websites were mostly for human readers and Google's bots to boost SEO, now various LLMs are continuously visiting and ingesting the information across the internet.

This information can then be highlighted to various users interacting with the LLMs — the clearer your site was for an LLM to understand, the better they can restate the key information and deliver value to the end user.

Optimization techniques can both increase your **visibility** and **correctness** of your website's information.

Choosing to not optimize your site runs the risk of LLMs incorrectly sharing some information about your tool or not surfacing your site, and instead your more prepared competitors.

Overall, your goal with your site is two fold:

1. 📊 To convey all of the useful information that can then be reconstituted by the LLM for the person using it
2. ⚡ To make your site easy to parse for quick LLM ingestion. Neither goal works in isolation.

Fortunately, steps taken to improve a website for LLMs either additionally help human readers or are completely invisible to them, therefore there is no downside to incorporating them.

## 📋 Prerequisites: similarities between content and site requirements

This article covers some website basics with one caveat: it skips some of the details on optimizing the content for LLMs. This has been covered in detail in a previous article.

Specifically, these topics include the importance of text that:

- 💬 is written in a conversational style
- ❓ contains FAQs, as this directly correlate to how people ask questions of LLMs
- 📈 uses quotes and statistics, which LLMs often include in their response. Both original and well-sourced existing quotes and stats.

For best results, take a moment to read through the short [Marketing Content overview](https://github.com/etelsv/GEO/blob/main/TechnicalMarketingContent.md).

## 🏗️ Structure and Language

### 🎯 Predictable information flow

When ingesting and parsing a page, LLMs can more effectively parse structures that allow them to easily summarize, paraphrase and work with in general.

Here predictability is your friend. Use your pages to effectively convey the value proposition of your product, and ensure, for example, that your homepage has clear, distinct sections that speak to your visitors' concerns:

- 🎯 the value proposition
- ⚙️ features
- 👥 social proof
- 📖 explanations

### 💬 Conversational Language

As LLMs interact with users asking questions in a conversational style, they process information that's written in a similar way more effectively. While products may be highly technical, being careful to explain concepts in normal business terms is helpful.

Similarly, jargon, acronyms without definitions, and any other language that may be difficult to interpret without deeper explanation should be avoided. Instead, define acronyms and terms up front.

### 📚 Consistent Site Vocabulary

While it was always a best practice to have a unified vocabulary, for LLMs, this makes it clear that if the same concept is referenced in different places then it nevertheless refers to the same thing.

Conversely, if one page calls it platform, the other a framework, and yet another a tool, the LLM may potentially get the takeaway that these are different items, and thus not be able to give the most precise information about it.

Unify your terminology at the outset and maintain an internal glossary of terms. This can be automated with a handy prompt:

` [**Your Website Here**]"Review this content and create a 'terminology guide' that lists: 1. The main product/feature names we use 2. Key phrases that appear multiple times 3. Any jargon or technical terms we define 4. Recommended standard language for each concept Then flag anywhere we deviate from these standards.`


## 📝 Content

### 🌐 Site Content

Use your site to contextualize your tool within the wider ecosystem. As LLMs analyze the relationships between entities (different concepts), providing additional information about where your tool sits in the ecosystem goes a long way. Make explicit, but neutral and professional:

- 🏆 comparisons between you and competitors
- 🔗 integrations to highlight how your tool works with relevant frameworks and libraries
- 📍 additional information about where in the stack your tool lives and how it connects to the ecosystem that your ideal customer has

The more information you can add there - potentially as separate landing pages- the more information an LLM can draw on, even if the question posed to them was not about your tool at all, but for example, alternatives to your competitor's offering.

Since your goal should be to make it as easy as possible for an LLM to paraphrase what your company does and how it works. It's worth taking the time to ensure that you're:

- 🎯 writing self-contained and useful messaging: don't make the reader or the LLM traverse your site to find key information. Keep what's relevant front and center.
- 📋 describing specific example, use cases, and explanations: where you can go out of your way to clarify the impact or value, do so. What might be implicit for a human reader may be well served by additional explanations that the LLM can then share.
    - 💡 It is in fact these use cases that may cause an LLM to surface your content. A question like: "_As a backend engineer, how can I solve my PostgreSQL database throttling our payment processing from 1,000 to 500 transactions per minute when I need better performance without making code changes?."_ may correlate to that exact use case on the _FooBarDB_ site.

### 🔄 Updating

As you change or update your main website the changes should come to light in most LLM responses. This is due to the difference in how the LLMs retrieve information. While the data sets of large LLMs update rarely, potentially annually, the use of real time web search in the conversations with LLMs means that as soon as an LLM can use a search engine to reach the page (Google for Gemini, Bing for ChatGPT, Brave Search for Claude, Perplexity bot for Perplexity), those interacting with an LLM can see it.

However, as an LLM pulls information not just from the homepage of company but from all over the internet, it's possible outdated messaging and information can be mixed into the results.

With this in mind: when you make big changes and launches, use that opportunity to also update the relevant information around the internet on the topic. This has two advantages:

1. 🎯 It ensures that the messaging that an LLM is pulling is consistent both on and off platform
2. 🔄 It also keeps relevant product content that is active and maintained, which increases the likelihood that LLMs will surface current content

## ⚙️ Tech considerations

In addition to the details of the text and set up of the website there are some basic tech implementation details that are valuable to ensure that you're not sabotaging your site's visibility through a simple change.

### 🤖 robots.txt

Robots.txt can be used to politely ask LLM bots to not crawl your site, in something along the following.

```
# Block major LLM/AI training bots
User-agent: GPTBot
Disallow: /

User-agent: anthropic-ai
Disallow: /

User-agent: Claude-Web
Disallow: /

# Allow regular search engines (optional)
User-agent: Googlebot
Allow: /

User-agent: *
Disallow:
```

**🚨 As we want to achieve the opposite, confirm that there are no lines that block them.**

On the other hand, if you have sites that don't contain valuable information and might slow down a crawler (like a calendar), you can also explicitly block access. Here's an example:

```
# Block low-value pages that waste crawl budget
User-agent: *
Disallow: /admin/
Disallow: /dashboard/
Disallow: /auth/
Disallow: /login/
Disallow: /signup/
Disallow: /settings/
Disallow: /account/
```

If you want to go deeper into this, you can see the results of a query like:

`If I have a dev tool website, how could I use the robots.txt to help LLM engines crawl it more efficiently?`

### 📄 llms.txt (same text as in [[FINAL - GEO for Documentation]])

There should also be an `llms.txt` file for the **entire** site that covers all of the site links in one clean document. The `llms.txt` file has a specific format that needs to be adhered to. The originator, [https://llmstxt.org/](https://llmstxt.org/), explains on their website where it should be located, what markdown formatting it should use and provides an example.

> **📋 llms.txt Specification**
> 
> The llms.txt file spec is for files located in the root path `/llms.txt` of a website (or, optionally, in a subpath). A file following the spec contains the following sections as markdown, in the specific order:
> 
> - An H1 with the name of the project or site. This is the only required section
> - A blockquote with a short summary of the project, containing key information necessary for understanding the rest of the file
> - Zero or more markdown sections (e.g. paragraphs, lists, etc) of any type except headings, containing more detailed information about the project and how to interpret the provided files
> - Zero or more markdown sections delimited by H2 headers, containing "file lists" of URLs where further detail is available
>     - Each "file list" is a markdown list, containing a required markdown hyperlink `[name](url)`, then optionally a `:` and notes about the file.

> **📘 Example llms.txt Format**

> ```
> # Title
> ```

> > Optional description goes here

> Optional details go here

> ## Section name

> - [Link title](https://link_url/): Optional link details

> ## Optional

> - [Link title](https://link_url/)

```

> 📝 **Note:** The "Optional" section has a special meaning—if it's included, the URLs provided there can be skipped if a shorter context is needed. Use it for secondary information which can often be skipped.
```

### 🏷️ Semantic HTML and Headers

Semantic HTML also helps the LLM quickly understand the key takeaways on your site pages.

Take the time to explicitly label different sections of the text to really highlight the key messages for the LLM.

Furthermore, unlike humans, LLMs cannot use spacing to infer hierarchy. This means that they cannot tell which information is subordinate to what came before and which is actually the beginning of a new section

Thus, headers are also useful for showing information hierarchy and to help the LLM understand what fits within each topic bucket.

A misplaced header can cause an LLM to misattribute concepts, while well-placed ones throughout speed up an LLM's ingestion of the information.

Below you can see a basic example with more specific labels (`<header>`, `<main>`, `<section>`, `<article>`, `<aside>` and headers `<h1>`,`<h2>`,`<h3>`) replacing the standard `<div>`.

Such labeling helps the bot clearly understand the details of the site and the relationship of the different sections to each other.

#### ❌ Before (without semantic HTML and clear headers)

```html
<div style="background: blue; color: white;">
  <div>FooBarDB</div>
  <div>3x faster than PostgreSQL, zero code changes</div>
</div>

<div>
  <div>Benefits</div>
  <div>Performance: 3x faster queries</div>
  <div>Portability: Drop-in SQL replacement</div>
  
  <div>const db = new FooBarDB('connection-string');</div>
  
  <div>"60% faster queries" — Sarah, TechFlow CTO</div>
  
  <div>Pricing</div>
  <div>Starter: $49/month</div>
  <div>Pro: $199/month</div>
</div>
```

#### ✅ After (with semantic HTML and clear headers)

```html
<header>
  <h1>FooBarDB</h1>
  <p>3x faster than PostgreSQL, zero code changes</p>
</header>

<main>
  <section id="features">
    <h2>Benefits</h2>
    <article>
      <h3>Performance</h3>
      <p>3x faster queries</p>
    </article>
    <article>
      <h3>Portability</h3>
      <p>Drop-in SQL replacement</p>
    </article>
  </section>

  <section>
    <pre><code>const db = new FooBarDB('connection-string');</code></pre>
  </section>

  <aside>
    <blockquote>"60% faster queries" <cite>— Sarah, TechFlow CTO</cite></blockquote>
  </aside>

  <section id="pricing">
    <h2>Pricing</h2>
    <article>Starter: $49/month</article>
    <article>Pro: $199/month</article>
  </section>
</main>
```

### 🔗 Internal Linking

While backlinks to your content are no longer paramount as they were with SEO, although there still is value in them beyond the scope of this article, internal site linking is helpful for bots to get a clearer picture of the site information hierarchy and further refine how concepts are interrelated.

It also avoids orphaned pages — pages on your site that have no links to them.

The recommendation is generally no more than 1-2 links per 1000 words.

This [Reddit post on internal linking](https://www.reddit.com/r/SEO/comments/1kh6c4m/i_made_an_awesome_chatgpt_prompt_for_internal/) offers a helpful prompt to analyze your pages and get some suggestions for interlinking. The results may be a bit 'over-enthusiastic' so you should use your own judgement to determine which links you do actually want to incorporate.

### ⚡ Fast Loading

Just as with SEO, fast loading is important in the GEO. However, the page speed is less google's interpretation of a good user experience but instead what allows bots to take in more content in the time they have on the page.

Bots are limited in the amount of time they have, and if pages load slowly, they may just use the information they were able to access. Similarly, if pages are exceptionally slow, bots may time out meaning that the end user may not get the information from that page in the response.

You can use https://pagespeed.web.dev/ to quickly review your own page loading speed and incorporate the relevant suggestions.

### 📊 Schemas

Schemas defined in the site code offer LLM bots definitive information about content on your site without them needing to analyze all of the content on a page. Using [JSON-LD](https://json-ld.org/), you can define the key things you want quickly surfaceable. Some relevant schema options could be:

- 🔗 `sameAs` which confirms that your company's presence on other sites

```JSON
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "FooBarDB",
  "description": "3x faster than PostgreSQL, zero code changes required",
  "applicationCategory": "DeveloperApplication",
  "operatingSystem": "Any",
  "programmingLanguage": "SQL",
  "sameAs": [
    "https://linkedin.com/company/foobardb",
    "https://github.com/foobardb",
    "https://twitter.com/foobardb"
  ]
}
```

- 💰 pricing, where you can quickly highlight the costs and benefits of different plans
- ❓ FAQs and How Tos, where you can quickly make key educational information surfaceable

This is a topic that one can dive very deeply into. For more actionable next steps, you can use these two prompts as a kick off:

#### 🛠️ How to implement schemas

`You are a senior full-stack developer specializing in SEO automation for developer tools. I'm the CEO of a developer tool company and need to automatically add JSON-LD schemas to our main website without manual coding for each page. Please provide: 1. **Technical Architecture**: Step-by-step implementation plan for automatic schema generation 2. **Code Solutions**: Ready-to-use code examples for: - Auto-detecting page types (homepage, product pages, documentation, pricing) - Generating appropriate schemas based on page content - Injecting schemas without manual intervention 3. **CMS Integration**: How to integrate with common tech stacks (Next.js, React, WordPress, etc.) 4. **Maintenance Strategy**: How to keep schemas updated automatically when content changes Requirements: - Must work across different page types - Should auto-populate from existing page data - Needs to be maintainable by non-technical team members - Should generate valid Schema.org markup Focus on practical, production-ready solutions that can be implemented quickly.`

#### 🎯 What schemas are most relevant for a developer tool company

`You are an SEO specialist who focuses exclusively on developer tools and B2B SaaS companies. I'm the CEO of a developer tool company and need to prioritize which JSON-LD schemas will have the biggest impact on our search visibility and conversions. Please provide: 1. **Priority-Ranked Schema List**: Top 10 most important schemas for developer tools, ranked by: - SEO impact potential - Conversion influence - Implementation difficulty - Competitive advantage 2. **Developer-Specific Schemas**: Schemas that specifically target developer searches like: - API documentation - Integration guides - Code examples - Technical tutorials 3. **Business Impact Analysis**: For each schema type, explain: - What search queries it targets - How it appears in search results - Expected business impact (traffic, conversions, brand authority) 4. **Quick Wins**: Which 3 schemas should we implement first for maximum ROI? Context: We're a developer tool company competing for developer attention and need to stand out in technical searches. Focus on schemas that developers actually search for and that influence their tool adoption decisions.`

## 📈 Tracking

In a former SEO dominated world, you could see people visiting your website from Google SEO efforts, from links found across the web, and from direct traffic within your analytics tool of choice. Now with more links coming from LLMs, you can segment that traffic using some premade regex (source: [Reddit post](https://www.reddit.com/r/OpenAI/comments/1jlt5yi/easy_way_to_track_chatgpt_traffic_in_google/))

```
^.*\.openai.*|.*copilot.*|.*chatgpt.*|.*gemini.*|.*gpt.*|.*neeva.*|.*writesonic.*|.*nimble.*|.*perplexity.*|.*google.*bard.*|.*bard.*google.*|.*bard.*|.*edgeservices.*|.*bnngpt.*|.*gemini.*google.*|.*claude.*|.*anthropic.*$
```

This should catch referrals to your site using many of the main LLM tools and show how much of your traffic is coming from LLMs as opposed to more traditional channels.

Note: This is the flip side of monitoring the brand mentions using an LLM tool, which shows your visibility among the prompts. This is key to set up because it shows your strengths against your competitors while tracking from your internal analytics gives you a better understanding of the overall most impactful marketing channels to drive site visitors. They are not interchangeable.

## 📚 Sources

- https://www.conductor.com/academy/robotstxt/faq/example-file/
- https://www.privacyjournal.net/block-llm-crawlers/
- https://techstartups.com/2025/05/28/from-seo-to-generative-engine-optimization-geo-why-the-new-era-of-search-belongs-to-ai-and-how-to-stay-visible/
- https://techstartups.com/2025/05/30/where-llms-get-the-real-time-data-behind-ai-search-and-why-it-matters-more-than-you-think/
- https://searchengineland.com/llms-txt-isnt-robots-txt-its-a-treasure-map-for-ai-456586
- https://writesonic.com/blog/llm-txt-guide
- https://fireup.pro/news/llms-txt-a-new-way-to-manage-ai-access-to-your-content-and-how-it-differs-from-robots-txt
- https://searchengineland.com/crawlers-search-engines-generative-ai-companies-429389
- https://semking.com/json-ld-google-tag-manager-no-ssr-invisible-ai-crawlers/
- https://www.airops.com/blog/using-ai-to-improve-seo-exploring-internal-links-and-backlinks
- https://github.com/romansky/dom-to-semantic-markdown?tab=readme-ov-file
- https://www.reddit.com/r/OpenAI/comments/1jlt5yi/easy_way_to_track_chatgpt_traffic_in_google/
