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
    <a href="./#about">About</a>
    <a class="nav-resume" href="./assets/Shawn-Lindsey-Resume.pdf">Resume ↗</a>
  </div>
</nav>

<div class="portfolio-shell case-study">

<section class="case-hero">
  <a class="case-back" href="./#work">← Selected work</a>

  <p class="eyebrow">AI + Documentation · 01</p>

  <h1>AI-Assisted<br>Documentation<br>Review Agent</h1>

  <p class="case-deck">
    A Claude-based review workflow designed to improve documentation
    consistency, reduce repetitive manual review, and make technical
    feedback more focused and actionable.
  </p>

  <div class="case-meta">
    <div>
      <span class="meta-label">Role</span>
      <strong>Technical Writer<br>Agent Designer</strong>
    </div>
    <div>
      <span class="meta-label">Environment</span>
      <strong>Claude<br>Git / Markdown</strong>
    </div>
    <div>
      <span class="meta-label">Focus</span>
      <strong>AI Workflows<br>Docs-as-Code</strong>
    </div>
  </div>
</section>


<section class="case-section case-intro">
  <p class="case-label">The problem</p>

  <div class="case-section-content">
    <h2>Technical reviews involve a lot of important, repetitive checks.</h2>

    <p class="case-lead">
      Documentation changes need to be checked for more than grammar.
      Writers have to consider implementation details, authentication,
      prerequisites, configuration, API behavior, and established
      documentation conventions.
    </p>

    <p>
      The goal of this project was to explore whether an AI-assisted
      reviewer could handle some of those repeatable checks while keeping
      the technical writer in control of the final documentation.
    </p>
  </div>
</section>


<section class="case-section">
  <p class="case-label">The approach</p>

  <div class="case-section-content">
    <h2>Make the review narrow, structured, and actionable.</h2>

    <p>
      Rather than asking an AI system to broadly review an entire
      documentation set, I designed the workflow around the changes
      already being made in Git.
    </p>

    <div class="case-principles">
      <div>
        <span>01</span>
        <h3>Scope the review</h3>
        <p>
          Use the current Git diff to focus analysis on modified
          documentation instead of reviewing unrelated content.
        </p>
      </div>

      <div>
        <span>02</span>
        <h3>Structure the findings</h3>
        <p>
          Categorize review output by severity and documentation area
          so writers can quickly identify the most important issues.
        </p>
      </div>

      <div>
        <span>03</span>
        <h3>Build in safeguards</h3>
        <p>
          Keep recommendations focused and actionable while preserving
          human review and approval before documentation changes are made.
        </p>
      </div>
    </div>
  </div>
</section>


<section class="case-section">
  <p class="case-label">Review coverage</p>

  <div class="case-section-content">
    <h2>Designed around the things technical writers actually review.</h2>

    <div class="case-check-grid">
      <div>
        <span>01</span>
        <strong>Onboarding</strong>
        <p>Prerequisites, setup steps, and missing context.</p>
      </div>

      <div>
        <span>02</span>
        <strong>Authentication</strong>
        <p>Authentication setup, requirements, and inconsistencies.</p>
      </div>

      <div>
        <span>03</span>
        <strong>API references</strong>
        <p>Outdated references, schema changes, and technical accuracy.</p>
      </div>

      <div>
        <span>04</span>
        <strong>Configuration</strong>
        <p>Settings, properties, dependencies, and unclear instructions.</p>
      </div>
    </div>
  </div>
</section>


<section class="case-section">
  <p class="case-label">Prompt design</p>

  <div class="case-section-content">
    <h2>Give the reviewer a specific job.</h2>

    <div class="prompt-block">
      <span class="prompt-label">Example review instruction</span>

      <p>
        Review the modified documentation files for outdated API references,
        missing prerequisites, authentication inconsistencies, schema drift,
        and unclear steps. Focus only on files changed in the current Git diff
        and prioritize actionable findings.
      </p>
    </div>

    <p>
      Prompt iteration focused heavily on controlling scope. The objective
      wasn't to maximize the amount of feedback—it was to make the feedback
      useful enough that a technical writer could act on it quickly.
    </p>
  </div>
</section>


<section class="case-visual-section">
  <div class="case-visual-heading">
    <p class="case-label">Example output</p>
    <p>Structured findings from a documentation review.</p>
  </div>

  <div class="case-large-visual">
    <img
      src="./assets/images/doc_review.png"
      alt="Example output from the AI-assisted documentation review agent">
  </div>
</section>


<section class="case-section">
  <p class="case-label">What I learned</p>

  <div class="case-section-content">
    <h2>More feedback isn't necessarily better feedback.</h2>

    <p class="case-lead">
      One of the biggest challenges was preventing the review from becoming
      overly verbose or repetitive.
    </p>

    <p>
      A significant part of the iteration process focused on improving
      clarity, consistency, and prioritization so that the output supported
      the writer's judgment instead of creating another layer of work.
    </p>
  </div>
</section>


<section class="case-section case-outcome">
  <p class="case-label">Outcome</p>

  <div class="case-section-content">
    <h2>From experiment to documentation workflow.</h2>

    <p class="case-lead">
      The resulting workflow concepts and review patterns were adopted
      across the documentation team to help streamline reviews, improve
      consistency, and reduce manual documentation overhead.
    </p>
  </div>
</section>


<nav class="case-pagination" aria-label="Project navigation">
  <a href="./#work">
    <span>Back</span>
    <strong>Selected work</strong>
  </a>

  <a class="next-project" href="./driver-documentation-dependency-resolver">
    <span>Next project</span>
    <strong>Documentation Dependency Resolver →</strong>
  </a>
</nav>

</div>
