
# 📚 GEO for Documentation

The way that developers are interacting with docs is changing. The expectation is now that the docs are the jumping off point and are augmented by the LLM of choice. In other words that the LLM will read the docs first and the developer will interact with the LLM itself as they build.

Thus, both for a use case of awareness building and for ease of use, producing good docs is more important than ever.

As stated by a talented tech writer in the industry, **"It's nice that people read the docs now."**

## 🎯 Core priorities for LLM-Optimized documentation

### 🔍 **Clarity**

Docs have to be structured in a clear way that is ingestible by an LLM. Have a clear cut structure make it easier for an LLM to browse the material and to give the correct answer. Care should also be taken that there are no things left out. Any explicit gaps in the documentation are opportunities for hallucination.

Furthermore, throughout the docs, it is beneficial to always refer to the same concept described by the same name. While stylistically, renaming something may make the text sound more elegant, this flourish confuses LLMs and should be avoided.

#### 💡 An example from Claude:

| 🚫 **Bad Example (Inconsistent Naming)** | ✅ **Good Example (Consistent Naming)** |
|---|---|
| *FoobarDB uses **connection pools** to manage database links. When configuring your **DB connections**, set the pool_size parameter. The connection manager will handle **client sessions** automatically. To monitor active **database handles**, use the get_connections() method* | *FoobarDB uses **connection pools** to manage database connections. When configuring your **connection pools**, set the pool_size parameter. The **connection pool** will handle client connections automatically. To monitor active connections, use the get_connections() method.* |

### 🏗️ **Structure**

Predictable structure also allows LLMs to provide the best results, as it follows a common pattern (for example quickstart → core concepts → comprehensive API reference → advanced examples). 

Originality in docs structure is not rewarded.

### 📦 **Self-contained**

Information should also be self-contained between sections. When ingesting information LLMs chunk it and can't always make the connection between things listed far earlier on a page or implied from a previous page. Where it does not conflict with readability, try making your information self contained, restating the core concepts the section is covering, or keeping information that is most relevant close to each other.

In the same way, take caution with pronouns that reference earlier concepts: _this, it that,_ etc. It's better to reuse the word in the sentence to ensure that the LLM can definitely reference the correct concept instead of trying to infer what "it" is referring to.

### ⚠️ **Avoid assumptions**

When in doubt, avoid making assumptions in the text. State prerequisites explicitly and when referencing other tooling, take a moment to explain what it is. LLMs work especially effectively when they deeply understand the relationships between different entities - this replaces that, this builds on that, this is similar to that, etc. 

### 📝 **Text over images**

LLMs cannot read images and thus when too much information is conveyed in a graphic, the LLMs miss that information. When possible it's best practice to either convey the information in text, or use alt text to describe what is being covered in the graphic. When referring back to what's in the image, lean on the concept of chunking, and restate in the text what the process that you are referencing from the image.

For example if you have a diagram about the authorization workflow (diagram left), ensure you have clear, parsable alt text.

> 💡 **The key insight:** *"treat LLMs like intelligent users who can read everything but are using a text-only browser"*

#### 🔐 Authorization flow example

| 🖼️ **Image**                                | 📋 **LLM-Readable Text**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![Authorization Flow Diagram](https://github-production-user-asset-6210df.s3.amazonaws.com/42931286/458812499-a7995a52-c946-4132-846a-434b8a6def71.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250902%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250902T110947Z&X-Amz-Expires=300&X-Amz-Signature=89dcf01c6c7e833b5832d80bc7f8b4e7118891101c6cbae54f0e72974fa3b2bf&X-Amz-SignedHeaders=host)| **Authorization Flow Summary**<br/>1. User initiates access request to an Identity Provider using OAuth 2.1/OIDC protocols<br/>2. Authentication occurs with multi-factor authentication and biometrics<br/>3. System issues a short-lived JWT/Access Token (with refresh token stored securely)<br/>4. Authorization Server applies role-based and attribute-based access controls (RBAC + ABAC)<br/>5. Policy Engine enforces Zero Trust principles and evaluates the request<br/>6. Risk Assessment analyzes context including, Device trust certificates, Location/network data, Behavioral patterns<br/>7. Decision Point based on risk level:<br/>   - Low risk → Direct resource access granted<br/>   - High risk → Step-up authentication required (additional verification)<br/>8. Continuous Monitoring tracks user behavior with analytics throughout the session<br/>9. All activities logged in Audit Logs for compliance<br/><br/>**Key Principle**<br/>The system maintains ongoing verification rather than one-time authentication, with contextual factors continuously influencing access decisions. |

### 💻 **Explain in code blocks**

LLMs prefer for the docs API information to be described within the code block rather than having the API endpoints done minimalistically with text explanation underneath. As always, keep relevant information as closely as possible together.

| 🚫 **Bad API Explanation** | ✅ **Good API Explanation** |
|---|---|
| **Connection**<br/><br/>Use the connect method to establish a connection.<br/><br/>```python<br/>db = FooBarDB.connect()``` | ```markdown<br/># Database Connection<br/><br/>**Purpose:** Establish connection to FooBarDB instance<br/><br/>**Authentication:** API key required (get yours at dashboard.foobardb.com)<br/><br/>```python<br/>import foobardb<br/><br/># Connect with API key<br/>db = foobardb.connect(<br/>    api_key="fbdb_1234567890abcdef",<br/>    host="api.foobardb.com"  # Optional: defaults to cloud instance<br/>)<br/><br/># Verify connection<br/>if db.is_connected():<br/>    print("Connected successfully") |

### 🚨 **Highlight errors and solutions**

In addition to writing about the optimal way to interact with the product in the docs, similarly to common SEO strategy, explicitly documenting errors can be extremely useful.

When hitting a snag, people often copy and paste the error exactly looking for a solution. When the LLM can directly diagnose the issue because it is documented and offer the solution, people can get back on track quickly.

On the other hand, with this information missing, LLMs may hallucinate or offer vague answers that may not necessarily be helpful and strain the trust between the developer and the product.

> ⚠️ **Important:** It's important to here to have the language be identical to the actual error rather than a general description of the kinds of errors one can encounter, as these may not always be surfaced as a resolution when interacting with the LLM.

## 🛠️ **Tooling**

When working with docs, you're set up for success when you have a markdown version of each page readily available for an LLM to browse. These should be generated at the same as you update your documentation.

Many companies just do this by having an additional version of the page with the same url that simply end in `.md`.

### 📄 **llms.txt**

There should also be an `llms.txt` file for the **entire** site that covers all of the site links in one clean doc. The `llms.txt` file has a specific format that needs to be adhered to. The originator, https://llmstxt.org/, explains on their website where it should be located, what markdown formatting it should use and provides and example.

> **📋 llms.txt specification**
> 
> The llms.txt file spec is for files located in the root path `/llms.txt` of a website (or, optionally, in a subpath). A file following the spec contains the following sections as markdown, in the specific order:
> 
> - An H1 with the name of the project or site. This is the only required section
> - A blockquote with a short summary of the project, containing key information necessary for understanding the rest of the file
> - Zero or more markdown sections (e.g. paragraphs, lists, etc) of any type except headings, containing more detailed information about the project and how to interpret the provided files
> - Zero or more markdown sections delimited by H2 headers, containing "file lists" of URLs where further detail is available
>     - Each "file list" is a markdown list, containing a required markdown hyperlink `[name](url)`, then optionally a `:` and notes about the file.

**📘 Example llms.txt Format**
 ```
# Title
> Optional description goes here

Optional details go here

## Section name

- [Link title](https://link_url): Optional link details

## Optional

- [Link title](https://link_url)
```

📝 **Note:** The "Optional" section has a special meaning—if it's included, the URLs provided there can be skipped if a shorter context is needed. Use it for secondary information which can often be skipped.


### 📄 llms-full.text

You can also make an `llms-full.txt` file where you collect all of the markdown files for all of your documentation into one single massive markdown file. This can then be copied and pasted by the reader of your docs into their LLM of choice. Now the LLM doesn't even have to retrieve your docs and has everything it needs to know to generate code from your docs or help the user debug their own code that refers to your documentation.

## 🌐 **Unified platform notes**

Ensure that all of your documentation are on a single site for easy retrieval. It may be possible that some docs may be located on your custom docs site (docs.foobar.io) while others on a docs platform (docusaurus). Alternately it could be from the process of migrating docs, or just having the information dispersed across various parts of the site (including blog, a quick start landing page etc).

This is very challenging for LLMs to ingest because they struggle to understand:

- **Which docs are most current or definitive.** They may highlight their indecision in their answer, linking the developer to multiple sources, putting more friction into dev process
- **The complete picture.** There is more overhead work for the LLM to understand how all the concepts interconnect - where there are tradeoffs, what syntax to say is definitive if there are contractions, when certain tools should be used over others. Such fragmentation leads to an LLM have a collection of facts about the tool with less comprehensive understanding, limiting their debugging and explanatory help.

## 🎁 **Bonus: Two additional ways to harness AI**

### 🔧 **Using AI for maintenance**

There's something interesting possible with deployments to documentation that is so well structured.

Whenever you push doc updates you can hook into an LLM and have it scan your existing docs and answer the the question:

> 🤖 `"Does this update contradict or make obselete any information in the current docs."`

This answer can help you keep your docs more updated in real-time even as their coverage grows.

### 📊 **Using AI for prioritization**

When considering making changes to an existing docs set, LLMs can be a helpful partner for a docs writer.

Even a simple prompt along the lines of:

> 🤖 `"Act as an LLM - what do you think of FooBarDB's docs. Are they easy to ingest and work with?"`

can begin to render some great constructive feedback or act as a vote of confidence for well-structured, well-written content.

Similarly asking the LLM to grade and review the documentation sites of companies you admire can deliver a nice summary of the best practices that they are using that can provide further inspiration for one's own work.

## 🔮 **Additional thoughts**

This summary provides the first overview of considerations when writing docs that are optimized for LLMs. However as with any subject, there is a lot more to learn. If you'd like to dive deeper, some topics that weren't covered here but may still be relevant are:

- **More details on chunking content.** This is actually very important and is worth a seperate deeper dive.
- **Optimizing for RAG** and preventing confusion in vector retrieval
- **Heirarchy**. TLDR: use a logical hierarchy, don't skip heading types unnecessarily (eg. ## to ####). There is more nuance here and it's worth learning. 
- **How to deal with version control.** Setting LLMs up for success with deprecation, migration pathways, changelogs
- **API Documentation.** There are a lot of specific details on how to write this especially effectively. 
- **Testing the efficacy of your docs**. Short version: asking an LLM: "Show me how to [common tool use case] with code examples". Long version: effective partnership with an LLM can really highlight some blindspots. 

## 📚 **Sources**

- [FusionAuth: LLMs for Docs](https://fusionauth.io/blog/llms-for-docs)
- [Kapa.ai: Writing Best Practices](https://docs.kapa.ai/improving/writing-best-practices)
- [DevDocs to LLM GitHub Project](https://github.com/alexfazio/devdocs-to-llm)
- [Everyone's Talking About llms.txt](https://dev.to/apilover/everyones-talking-about-llmstxt-here-is-what-i-experienced-4p7i)
- [AI the Docs 2024 Event](https://pronovix.com/event/ai-the-docs-2024)
- [llms.txt Official Specification](https://llmstxt.org/)
- [Mintlify: How to Improve LLM Readability](https://mintlify.com/blog/how-to-improve-llm-readability)
