# LinkedIn Job Seeker Skill Creation

1.

/skill-creator

let's create a new skill using the skill creator tool. Interview me with as many questions as needed to build the best functioning skill

2.

Create a skill that helps the user's to scrape for jobs on Linkedin using the , based on keywords, job titles and locations, then extracts the company name, job title, job link and posting date before adding everything into an organized spreadsheet automatically in real time. Use the user's own Linkedin account for personalized and localized results. As for the

1. Framework: Use the Model Context Protocol (MCP) as the standard, as it is native to Claude Desktop and Claude Code.
2. Browser Interface: Use an extension-based model like mcp-chrome or a locally bound Playwright MCP connected to the user's active profile. This guarantees that you are leveraging the user's logged-in session securely without requiring them to share their credentials with an external cloud service.
3. Human-like Pacing (Crucial for LinkedIn): Your MCP server's underlying tool code should enforce strict guardrails:
    * Limit the rate of page navigation (e.g., adding a randomized delay of 5 to 15 seconds between viewing different jobs).
    * Limit the total number of jobs parsed per session (e.g., maximum of 50–100 jobs a day) to stay well under LinkedIn's rate limits.
4. Data Extraction Strategy: Instead of having Claude click every job card one by one (which is slow, expensive, and looks like bot behavior), have Claude navigate to the search results page, then use Javascript execution via the MCP tool to extract the pre-loaded data object or parse the page source in bulk.

## A few decisions before I draft:

* Which browser interface should the skill target?
support both but use claude in chrome as default

* How should results be saved?
One master .xlsx (Recommended)

* Beyond company, title, link, and posting date — which extra fields should it capture when available?
Location & remote type, Easy Apply flag

* How should search parameters (keywords, titles, locations) work?
Ask each run (Recommended)

Good. A few final details, then I'll draft:
* Default cap on jobs collected per session?
50 (Recommended)


* Default 'date posted' filter for searches (overridable per run)?
Past week (Recommended)


* Should posting dates be stored as actual dates? LinkedIn only shows relative times like '3 days ago'.
Convert to real dates (Recommended)
