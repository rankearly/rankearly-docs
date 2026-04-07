---
title: "Content Writing"
description: "Best practices for using RankEarly's content writing skills to create blog posts that rank."
---

These skills work together as a pipeline: research, ideation, creation, optimization.

## The Content Writing Skills

| Skill | What you get | When to use |
|-------|-------------|-------------|
| [**content-researcher**](https://www.rankearly.pro/skills/content-researcher) | Two research files: a **knowledge base** summarizing what top-ranking pages already cover, and a list of **under-discussed questions** that competitors skip — with researched answers | You have a keyword or topic and want to know what's already out there and what's missing before you write |
| [**blog-creator**](https://www.rankearly.pro/skills/blog-creator) | A complete blog post — researched, outlined, written, and illustrated — saved to `blogs/<topic>/` | You want to go from a topic idea (or an existing outline) to a published-ready blog in one run |
| [**blog-title-generator**](https://www.rankearly.pro/skills/blog-title-generator) | 10 title options, each with a search-optimized title tag, a reader-friendly H1, scores across 5 dimensions, and a note on why it works | Your blog is drafted and you need a title that ranks well and gets clicks |
| [**blog-image**](https://www.rankearly.pro/skills/blog-image) | A ready-to-paste image generation prompt — either a cover image or a clean diagram/illustration | You need a hero image for the top of your post, or an explanatory visual for a section |

---

## Scenario A: Start from a keyword

You have a keyword but no idea what to write. Start with research.

```
/content-researcher keyword "email deliverability"
```

This reads the top-ranking pages and produces two files:

- **`knowledge-base.md`** — ~30 structured entries summarizing what existing content covers, each labeled by depth (H/M/L). Use this to understand the baseline — what readers already have access to.
- **`under-discussed.md`** — Questions that top results don't answer well, each with a researched answer. These are your **information gain** — the reason someone would read your post over the existing results.

Open `under-discussed.md`, pick a question that's relevant to your business, and hand it to the blog creator:

```
/blog-creator create a blog for the question "{question}" from under-discussed.md
```

The blog creator runs its own pipeline — SERP validation, research, outline, writing, and illustration — and saves everything under `blogs/<topic>/`. It pauses after the outline for your review before writing the full post.

This approach naturally fits GEO (Generative Engine Optimization), which favors specific Q&A over broad keyword-stuffing.

## Scenario B: Start from a topic idea

You have a topic in mind ("how SaaS companies should handle email authentication") but haven't done keyword research yet.

```
/blog-creator write a blog about how SaaS companies should handle email authentication
```

The blog creator handles everything from here:

1. **Finds the right keyword** — runs a SERP analysis to validate the topic and identify the best search query
2. **Researches competitors** — reads top-ranking pages and surfaces gaps via `/content-researcher`
3. **Builds an outline** — structures the post around your information gain, then pauses for your feedback
4. **Writes the post** — produces the full blog with natural product tie-ins (if SEO memory is set up)
5. **Adds illustrations** — identifies 1-3 sections that benefit from a visual and generates image prompts

You don't need to run `/content-researcher` separately — the blog creator calls it internally.

## Scenario C: Start from an existing outline

You've already planned the structure and just need someone to write it.

```
/blog-creator write a blog from this outline: blogs/email-auth/outline.md
```

This skips research and SERP analysis entirely. The blog creator goes straight to writing based on your outline, then adds illustration prompts where helpful.

## Scenario D: Improve a draft that feels thin

Your draft exists but lacks depth. The fix depends on how much work you want to redo.

**Light fix — expand specific sections yourself.** If you know which parts are weak, just ask Claude to flesh them out. No skill needed.

**Full rewrite — re-run the blog creator pipeline.** If the draft needs a fundamentally different angle or deeper research, run `/blog-creator` again for the same topic. This re-runs the full pipeline: SERP validation, content research (producing fresh `knowledge-base.md` and `under-discussed.md`), a new outline, and a full rewrite. The research step reads top-ranking pages and costs RankEarly credits, so only do this when the draft genuinely needs a new foundation — not just a few stronger paragraphs.

```
/blog-creator rewrite the blog at blogs/email-auth/blog.md — the current version is too thin
```

During the outline step, the skill pauses for your review. This is where you steer the rewrite — keep sections that worked, cut what didn't, and add new angles from the fresh `under-discussed.md`.

## Scenario E: Optimize your title after writing

Titles are easier to optimize once the post is written — you know exactly what it delivers.

```
/blog-title-generator for blogs/email-auth/blog.md
```

The skill offers two modes:

- **SERP mode** — analyzes the top 10 ranking titles for your keyword and generates titles that exploit gaps in what competitors are doing. Requires RankEarly MCP and may consume credits.
- **Quick mode** — generates titles immediately from proven formulas without SERP analysis. Good enough when you're iterating fast.

You'll get 10 scored variations with a recommendation on which ones to use and why.

## Scenario F: Add a cover image or illustration

```
/blog-image cover for "Keyword Clustering: The Complete Guide"
```

```
/blog-image illustration showing top-down vs bottom-up content strategy workflows
```

The skill generates an image prompt you can paste into the image generator. It supports blog covers and in-post diagrams/illustrations.

Note: `/blog-creator` already generates illustration images as its final step. You only need `/blog-image` separately for cover images or when working outside the blog creator pipeline.

---

## Win Keyword Clusters with Content Groups

A [keyword cluster](/glossary#keyword-cluster) is a group of related keywords. Most people write one blog post per keyword cluster, trying to cover all the related in a single article. That rarely works for competitive topics — one post can't go deep enough to beat pages that specialize.

**Write multiple posts per cluster instead.** Run `/content-researcher` on the cluster's primary keyword, and it'll surface questions that existing content doesn't answer well. Each of those questions becomes its own focused blog post.

Here's what that looks like in practice:

1. Run `/content-researcher` on the primary keyword of your cluster
2. Pick 3-5 under-discussed questions from the output
3. Create one blog per question using `/blog-creator`
4. Link all the posts together from a pillar page that covers the broad topic

You end up with a group of tightly related posts, each going deep on a specific angle — instead of one post trying to do everything. Search engines reward this depth.

## Keep Your SEO Memory Updated

SEO memory stores what your business does and how it helps people. This is a benefit-driven approach — instead of listing features, you map each capability to the benefit it provides. When `/blog-creator` writes content, it draws on this memory to naturally weave in relevant examples and proof points that fit the article's topic.

Before creating content, make sure your SEO memory reflects your current business:

```
/seo-memory extract from docs/about.md
```

Feed it factual sources — service descriptions, product docs, case studies, or anything that explains what you offer and who it helps. Not marketing fluff. The skill doesn't distinguish facts from spin.

## Typical End-to-End Workflow

Here's how a full content run looks from start to finish:

1. **Research the keyword.** Run `/content-researcher` on your target keyword. You'll get a knowledge base of what's already ranking and a list of under-discussed questions competitors miss.

2. **Pick a question.** Open `under-discussed.md` and choose a question that's relevant to your business.

3. **Create the blog.** Run `/blog-creator` with that question. It handles SERP validation, research, outlining, writing, and illustration — and pauses after the outline so you can steer the direction.

4. **Review and refine.** The finished blog and illustrations are saved to `blogs/<topic>/`. Read through and make any adjustments.

5. **Optimize the title.** Run `/blog-title-generator` on the finished blog to get 10 scored title options.

6. **Add a cover image.** Run `/blog-image` with your chosen title to generate a cover image prompt.
