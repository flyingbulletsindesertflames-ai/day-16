What We Did
We added a custom skill called s-stock-fundamental-research, designed specifically for analyzing Indian and global listed companies. Instead of typing out a long, detailed prompt every time (sector context, which metrics to pull, formatting rules, disclaimers), the skill bundles all of that into a single reusable instruction set that Claude reads automatically.
We tested it on five major Indian large-caps: TCS, Infosys, Reliance Industries, HDFC Bank, and Tata Motors. The skill's "Compare" mode was triggered, which produces a structured side-by-side report rather than five separate one-off analyses.

The output included:
A full comparison table covering CMP, market cap, P/E, P/B, revenue/profit CAGR, margins, ROE, ROCE, debt levels, dividend yield, and promoter holding
A "Where Each One Leads" section breaking down which company wins on profitability, growth, valuation, and risk
A neutral, advice-free summary explaining how the five companies aren't really substitutes for each other since they sit in different sectors
A short glossary explaining terms like ROE, ROCE, P/E, P/B, and OPM in plain English
A flag on Tata Motors' October 2025 demerger (passenger vehicles/JLR vs. commercial vehicles), since using the wrong post-split entity would have skewed the numbers
A real data-quality issue came up along the way: Tata Motors' corporate structure changed mid-2025, so the "right" ticker to use wasn't obvious. This is a good real-world reminder that automated research tools still need a human to sanity-check structural changes, not just pull numbers blindly.


What We Learned
Custom Skills = reusable instructions, not one-off prompts. Once defined, a skill enforces consistent rules (data sourcing priority, never giving buy/sell advice, always citing sources) across every future request, without re-explaining them each time.
Skills can encode entire frameworks. This one had a built-in research checklist (valuation, growth, balance sheet health, returns, ownership, peers) and interpretation rules (e.g., ROE/ROCE above 15% = Good, D/E above 2 = Leveraged). That's a financial analysis framework baked directly into the tool.
Mode-detection matters. The skill defines multiple output modes — Quick Take, Deep Dive, Compare, Pros & Cons, Portfolio Fit — and picks the right one based on how the request is phrased. A vague request ("analyze these 5 stocks") needs clarification before picking a mode; specificity upfront avoids wasted effort.
Guardrails are part of good skill design. This skill explicitly forbids investment advice, price targets, or predictions, and requires a disclaimer every time. That's a useful pattern for any AI workflow touching regulated or sensitive domains.
Real-world data has edge cases. Corporate actions (mergers, demergers) can break naive automation. The Tata Motors split was a good example of why "use live data, but verify structural assumptions" has to be a rule, not an afterthought.
