---
layout: default
title: AI-Assisted Documentation Review Agent
---

<nav class="site-nav" aria-label="Primary navigation">
  <a class="site-mark" href="./">SL</a>
  <div class="site-nav-links">
    <a href="./#work">Work</a>
    <a href="./#experience">Experience</a>
    <a href="./#writing">Writing</a>
    <a href="mailto:slindsey001@gmail.com">Email</a>
    <a href="https://www.linkedin.com/in/slindsey001/">LinkedIn</a>
    <a class="nav-resume" href="./assets/Shawn-Lindsey-Resume.pdf">Resume ↗</a>
  </div>
</nav>

<div class="portfolio-shell home proj">

<section class="proj-intro">
  <a class="proj-back" href="./#work">← Projects</a>
  <h1>AI-assisted documentation review agent</h1>
  <p class="home-lede">A Claude-based reviewer that checks only the files changed in the current Git diff and returns structured findings a writer can act on. The writer approves every change.</p>
  <dl class="proj-facts">
    <div><dt>Role</dt><dd>Designed and built it</dd></div>
    <div><dt>Tools</dt><dd>Claude, Git, Markdown</dd></div>
    <div><dt>Used by</dt><dd>The 11-person CData docs team</dd></div>
  </dl>
</section>

<section class="home-section">
  <h2>The problem</h2>
  <p>Reviewing a docs change means more than checking grammar. Writers also verify authentication steps, prerequisites, configuration, and API behavior. Most of those checks are important and repetitive, and they're where things slip. I wanted an AI reviewer to take on the repeatable checks without taking over the writer's judgment.</p>
</section>

<section class="home-section">
  <h2>How it works</h2>
  <ol class="proj-steps">
    <li><strong>Scoped to the diff.</strong> It reviews only files changed in the current Git diff, not the whole doc set.</li>
    <li><strong>Structured findings.</strong> Each issue has a category, a before and after, and a reason, sorted so the important ones come first.</li>
    <li><strong>Human in the loop.</strong> Nothing changes until the writer approves it.</li>
  </ol>
  <dl class="proj-checks">
    <div><dt>Onboarding</dt><dd>Prerequisites, setup steps, missing context</dd></div>
    <div><dt>Authentication</dt><dd>Setup requirements and inconsistencies</dd></div>
    <div><dt>API references</dt><dd>Outdated endpoints and schema drift</dd></div>
    <div><dt>Configuration</dt><dd>Properties, dependencies, unclear steps</dd></div>
  </dl>
</section>

<section class="home-section">
  <h2>Example findings</h2>
  <div class="proj-diff">
    <div class="proj-finding">
      <strong>Outdated endpoint</strong>
      <code class="proj-del">- Calls /v1/accounts.</code>
      <code class="proj-add">+ Calls GET /v2/accounts.</code>
      <span>/v1 was deprecated in build 9123; the docs lagged.</span>
    </div>
    <div class="proj-finding">
      <strong>Hardcoded secret in sample</strong>
      <code class="proj-del">- Password=MyP@ssw0rd!</code>
      <code class="proj-add">+ Password=&lt;your-password&gt;</code>
      <span>Copy-paste samples were leaking placeholder credentials into configs.</span>
    </div>
    <div class="proj-finding">
      <strong>Schema drift</strong>
      <code class="proj-del">- CreatedDate returned as string.</code>
      <code class="proj-add">+ CreatedDate returned as datetime.</code>
      <span>Type changed in build 9088; ADO.NET users got cast errors.</span>
    </div>
  </div>
</section>

<section class="home-section">
  <h2>The prompt</h2>
  <p>Most iteration went into controlling scope. The goal was feedback a writer could act on quickly, not more feedback.</p>
  <pre class="proj-code">Review the modified documentation files for outdated API references, missing prerequisites, authentication inconsistencies, schema drift, and unclear steps. Focus only on files changed in the current Git diff and prioritize actionable findings.</pre>
</section>

<section class="home-section">
  <h2>Result</h2>
  <p>The agent is now part of the docs team's review workflow, catching about <mark class="ph">5</mark> issues per review across <mark class="ph">200+</mark> reviews and cutting review time by about <mark class="ph">30%</mark>. The biggest lesson: early versions were verbose, and most of the work was making the output shorter, more consistent, and better prioritized.</p>
</section>

<div class="proj-pager">
  <a href="./#work">← All projects</a>
  <a href="./driver-documentation-dependency-resolver">Next: Documentation dependency resolver →</a>
</div>

</div>
