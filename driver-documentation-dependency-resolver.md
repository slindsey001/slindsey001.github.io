---
layout: default
title: Driver Documentation Dependency Resolver
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

  <p class="eyebrow">Documentation Infrastructure · 02</p>

  <h1>Documentation<br>Dependency<br>Resolver</h1>

  <p class="case-deck">
    A static analysis tool for tracing shared documentation dependencies
    across more than 300 product documentation builds.
  </p>

  <div class="case-meta">
    <div>
      <span class="meta-label">Role</span>
      <strong>Technical Writer<br>Tool Designer</strong>
    </div>
    <div>
      <span class="meta-label">Stack</span>
      <strong>Python<br>HTML / JavaScript</strong>
    </div>
    <div>
      <span class="meta-label">Focus</span>
      <strong>Docs-as-Code<br>Impact Analysis</strong>
    </div>
  </div>
</section>


<section class="case-section">
  <p class="case-label">The problem</p>

  <div class="case-section-content">
    <h2>One shared file can affect dozens of products.</h2>

    <p class="case-lead">
      CData documentation is assembled from shared content that can be reused
      across a catalog of more than 300 database drivers.
    </p>

    <p>
      Shared files are pulled into builds through multiple layers of includes,
      entities, bundles, chapters, and conditional rules. That made a seemingly
      simple question surprisingly difficult to answer:
    </p>

    <div class="prompt-block">
      <span class="prompt-label">Core question</span>
      <p>Which drivers use this shared documentation file?</p>
    </div>

    <p>
      Before this tool, answering that question often required repository-wide
      searches and manual investigation. The project focused on making those
      dependencies immediately visible so writers could understand the impact
      of a change before making it.
    </p>
  </div>
</section>


<section class="case-section">
  <p class="case-label">The model</p>

  <div class="case-section-content">
    <h2>Resolve the build process, then invert it.</h2>

    <p class="case-lead">
      The documentation system already knows how to answer one direction:
      what content is included in a given driver build.
    </p>

    <p>
      I modeled that assembly process across the driver catalog, followed each
      reference transitively into shared content, and then inverted the result
      to answer the question from the other direction.
    </p>

    <div class="case-principles">
      <div>
        <span>01</span>
        <h3>Trace references</h3>
        <p>
          Follow shared bundles, chapter includes, inline entities, and other
          references across the documentation tree.
        </p>
      </div>

      <div>
        <span>02</span>
        <h3>Evaluate conditions</h3>
        <p>
          Respect edition-specific and build-specific conditional content
          instead of treating every possible reference as active.
        </p>
      </div>

      <div>
        <span>03</span>
        <h3>Invert the graph</h3>
        <p>
          Convert the resolved dependency model into a lookup that shows which
          drivers consume any given shared file.
        </p>
      </div>
    </div>
  </div>
</section>


<section class="case-section">
  <p class="case-label">Resolution logic</p>

  <div class="case-section-content">
    <h2>Designed for the actual complexity of the documentation system.</h2>

    <div class="case-check-grid">
      <div>
        <span>01</span>
        <strong>Transitive resolution</strong>
        <p>
          Resolves dependencies across bundles, chapters, shared maps, and
          inline entities.
        </p>
      </div>

      <div>
        <span>02</span>
        <strong>Authoritative lookup</strong>
        <p>
          Uses generated build indexes rather than relying on file-name
          conventions.
        </p>
      </div>

      <div>
        <span>03</span>
        <strong>Conditional content</strong>
        <p>
          Evaluates edition-specific and build-specific inclusion rules.
        </p>
      </div>

      <div>
        <span>04</span>
        <strong>Attribution</strong>
        <p>
          Tracks how each dependency was reached so results remain explainable.
        </p>
      </div>
    </div>
  </div>
</section>


<section class="case-section">
  <p class="case-label">CLI workflow</p>

  <div class="case-section-content">
    <h2>Turn a repository-wide investigation into one command.</h2>

    <p>
      The command-line tool accepts the path to a shared documentation file
      and returns the drivers that consume it, along with how each dependency
      was reached.
    </p>

    <div class="prompt-block">
      <span class="prompt-label">Example command</span>
      <p>python doc-deps.py AzureProps/AzureAccessKey.prp</p>
    </div>

    <div class="code-output">
<pre>File:   ProviderBase/help/source/AzureProps/AzureAccessKey.prp
Entity: &amp;AZUREPROPSpAzureAccessKey;
Via:    mixed

Direct body reference (3):
  ProviderDatabricks
  SyncADLS
  SyncAzureBlobDestination

Via shared .map, marked-section gated (10):
  ProviderAccess
  ProviderAvro
  ProviderCSV
  ProviderExcel
  ProviderJSON
  ProviderParquet
  ProviderREST
  ProviderSASDataSets
  ProviderSASXpt
  ProviderXML</pre>
    </div>
  </div>
</section>


<section class="case-visual-section">
  <div class="case-visual-heading">
    <p class="case-label">Web interface</p>
    <p>Searchable dependency results with visual path attribution.</p>
  </div>

  <div class="case-large-visual case-large-visual--ui">
    <img
      src="./assets/images/doc_resolver.png"
      alt="Searchable web interface for the Documentation Dependency Resolver">
  </div>
</section>


<section class="case-section">
  <p class="case-label">Validation</p>

  <div class="case-section-content">
    <h2>Accuracy mattered more than coverage claims.</h2>

    <p class="case-lead">
      One of the hardest parts of the project was correctly evaluating
      conditional content.
    </p>

    <p>
      Early versions treated some edition-specific conditions too broadly,
      which produced dependency gaps. I compared resolver output against
      ground-truth repository searches to find those discrepancies and refine
      the resolution model.
    </p>

    <p>
      The project also reinforced the importance of clearly communicating
      limitations. Some content is generated by the build process itself and
      cannot be traced through ordinary references, so the tool explicitly
      identifies unresolved and build-generated cases rather than overstating
      certainty.
    </p>
  </div>
</section>


<section class="case-section case-outcome">
  <p class="case-label">Outcome</p>

  <div class="case-section-content">
    <h2>From manual search to instant impact analysis.</h2>

    <p class="case-lead">
      The final tool includes both a command-line resolver and searchable web
      interface capable of tracing documentation dependencies across 307 drivers.
    </p>

    <div class="case-stats">
      <div>
        <strong>307</strong>
        <span>drivers analyzed</span>
      </div>

      <div>
        <strong>~98%</strong>
        <span>of referenced shared files resolved</span>
      </div>

      <div>
        <strong>Seconds</strong>
        <span>instead of manual repository investigation</span>
      </div>
    </div>

    <p>
      The resolver supports documentation impact analysis, dependency discovery,
      and identification of shared or potentially orphaned content.
    </p>
  </div>
</section>


<nav class="case-pagination" aria-label="Project navigation">
  <a href="./ai-documentation-agent">
    <span>Previous project</span>
    <strong>← AI-Assisted Documentation Review Agent</strong>
  </a>

  <a class="next-project" href="./#work">
    <span>Back</span>
    <strong>Selected work →</strong>
  </a>
</nav>

</div>
