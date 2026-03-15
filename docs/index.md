---
title: AIVA – AI-Powered Genomics Platform
description: Comprehensive documentation for AIVA - AI-powered genomic data visualization and analysis platform
hide:
  - navigation
  - toc
---

<!-- HERO -->
<section class="aiva-hero">
  <span class="aiva-hero__eyebrow">AI-Powered Genomics</span>
  <h1>Precision genomics, <span>reimagined with AI</span></h1>
  <p class="aiva-hero__sub">Upload VCFs, explore millions of variants in real time, chat with an AI assistant that understands your data, and generate clinical-grade reports — all in one platform.</p>
  <div class="aiva-hero__actions">
    <a href="getting-started/" class="aiva-btn aiva-btn--primary">Get Started →</a>
    <a href="aiva-chat/" class="aiva-btn aiva-btn--ghost">Explore AIVA Chat</a>
  </div>
  <div class="aiva-hero__stats">
    <div class="aiva-hero__stat">
      <span class="aiva-stat__value">50M+</span>
      <span class="aiva-stat__label">Variants per sample</span>
    </div>
    <div class="aiva-hero__stat">
      <span class="aiva-stat__value">&lt;&thinsp;2s</span>
      <span class="aiva-stat__label">Query response time</span>
    </div>
    <div class="aiva-hero__stat">
      <span class="aiva-stat__value">HIPAA</span>
      <span class="aiva-stat__label">Compliant &amp; auditable</span>
    </div>
    <div class="aiva-hero__stat">
      <span class="aiva-stat__value">10+</span>
      <span class="aiva-stat__label">AI tools built-in</span>
    </div>
  </div>
</section>

<!-- METRICS BAR -->
<div class="aiva-metrics">
  <div class="aiva-metric">
    <span class="aiva-metric__value">VCF · CSV · TSV</span>
    <span class="aiva-metric__label">Supported file formats</span>
  </div>
  <div class="aiva-metric">
    <span class="aiva-metric__value">VEP + AnnotSV</span>
    <span class="aiva-metric__label">Annotation engines</span>
  </div>
  <div class="aiva-metric">
    <span class="aiva-metric__value">ACMG/AMP</span>
    <span class="aiva-metric__label">Classification standard</span>
  </div>
  <div class="aiva-metric">
    <span class="aiva-metric__value">REST API</span>
    <span class="aiva-metric__label">Full programmatic access</span>
  </div>
</div>

<!-- FEATURE 1 – AIVA CHAT -->
<div class="aiva-feature">
  <div class="aiva-feature__visual">
    <div class="aiva-feature__mockup">
      <div class="aiva-mockup__bar">
        <span class="aiva-mockup__dot aiva-mockup__dot--red"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--yellow"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--green"></span>
        <span class="aiva-mockup__title">AIVA Chat</span>
      </div>
      <div class="aiva-mockup__body">
        <div class="aiva-chat__msg aiva-chat__msg--user">Which variants have ACMG class ≥ 4?</div>
        <div class="aiva-chat__msg aiva-chat__msg--ai">
          <span class="aiva-chat__label">AIVA</span>
          Found 12 pathogenic variants. Showing top results by CADD score…
        </div>
        <div class="aiva-chat__rows">
          <div class="aiva-chat__row">
            <span class="aiva-chat__gene">BRCA1</span>
            <span class="aiva-badge aiva-badge--path">Pathogenic</span>
          </div>
          <div class="aiva-chat__row">
            <span class="aiva-chat__gene">TP53</span>
            <span class="aiva-badge aiva-badge--path">Pathogenic</span>
          </div>
          <div class="aiva-chat__row">
            <span class="aiva-chat__gene">MLH1</span>
            <span class="aiva-badge aiva-badge--lpath">Likely Pathogenic</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="aiva-feature__body">
    <span class="aiva-feature__label">AI Assistant</span>
    <h2 class="aiva-feature__title">Your genomics expert, always on</h2>
    <p class="aiva-feature__desc">AIVA Chat is a purpose-built AI assistant that understands your variant data. Ask natural-language questions, run Python code, search literature, and annotate variants — without leaving the platform.</p>
    <ul class="aiva-feature__bullets">
      <li>Query millions of rows with plain-English prompts</li>
      <li>PubTator biomedical literature search built-in</li>
      <li>Phenotype-to-gene prioritization via Phen2Gene</li>
      <li>Knowledge graph exploration for variant context</li>
      <li>Code interpreter for custom analysis scripts</li>
    </ul>
    <a href="aiva-chat/" class="aiva-feature__link">Explore AIVA Chat →</a>
  </div>
</div>

<!-- FEATURE 2 – DATA TABLE (reversed) -->
<div class="aiva-feature aiva-feature--reverse">
  <div class="aiva-feature__visual">
    <div class="aiva-feature__mockup">
      <div class="aiva-mockup__bar">
        <span class="aiva-mockup__dot aiva-mockup__dot--red"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--yellow"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--green"></span>
        <span class="aiva-mockup__title">Variant Table</span>
      </div>
      <div class="aiva-mockup__body">
        <div class="aiva-tbl__head">
          <span>Gene</span><span>CHROM</span><span>CADD</span><span>Class</span>
        </div>
        <div class="aiva-tbl__row">
          <span>BRCA2</span><span>13q12</span><span>34.2</span>
          <span class="aiva-badge aiva-badge--path">Path</span>
        </div>
        <div class="aiva-tbl__row aiva-tbl__row--alt">
          <span>PTEN</span><span>10q23</span><span>28.7</span>
          <span class="aiva-badge aiva-badge--lpath">LP</span>
        </div>
        <div class="aiva-tbl__row">
          <span>APC</span><span>5q22</span><span>22.1</span>
          <span class="aiva-badge aiva-badge--vus">VUS</span>
        </div>
        <div class="aiva-tbl__row aiva-tbl__row--alt">
          <span>RB1</span><span>13q14</span><span>19.4</span>
          <span class="aiva-badge aiva-badge--vus">VUS</span>
        </div>
        <div class="aiva-tbl__foot">50M+ rows · real-time filtering</div>
      </div>
    </div>
  </div>
  <div class="aiva-feature__body">
    <span class="aiva-feature__label">Data Table</span>
    <h2 class="aiva-feature__title">Millions of rows. Zero lag.</h2>
    <p class="aiva-feature__desc">AIVA's virtualized data table renders large cohorts instantly. Filter, sort, flag, and comment at the row level — with full keyboard navigation and one-click exports.</p>
    <ul class="aiva-feature__bullets">
      <li>Handles 50M+ variant rows without pagination</li>
      <li>Multi-column filters with Boolean logic</li>
      <li>Export filtered views to CSV or TSV</li>
      <li>Inline threaded comments per variant row</li>
    </ul>
    <a href="data-table/" class="aiva-feature__link">Explore the Data Table →</a>
  </div>
</div>

<!-- FEATURE 3 – ANALYSIS -->
<div class="aiva-feature">
  <div class="aiva-feature__visual">
    <div class="aiva-feature__mockup">
      <div class="aiva-mockup__bar">
        <span class="aiva-mockup__dot aiva-mockup__dot--red"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--yellow"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--green"></span>
        <span class="aiva-mockup__title">Analysis Hub</span>
      </div>
      <div class="aiva-mockup__body">
        <div class="aiva-hub__grid">
          <div class="aiva-hub__card">
            <div class="aiva-hub__icon aiva-hub__icon--acmg"></div>
            <span>ACMG/AMP</span>
          </div>
          <div class="aiva-hub__card">
            <div class="aiva-hub__icon aiva-hub__icon--pgx"></div>
            <span>PGx Panel</span>
          </div>
          <div class="aiva-hub__card">
            <div class="aiva-hub__icon aiva-hub__icon--sv"></div>
            <span>Struct. Vars</span>
          </div>
          <div class="aiva-hub__card">
            <div class="aiva-hub__icon aiva-hub__icon--cat"></div>
            <span>Categories</span>
          </div>
        </div>
        <div class="aiva-hub__bar-chart">
          <div class="aiva-hub__bar" style="height:70%"></div>
          <div class="aiva-hub__bar" style="height:45%"></div>
          <div class="aiva-hub__bar" style="height:85%"></div>
          <div class="aiva-hub__bar" style="height:55%"></div>
          <div class="aiva-hub__bar" style="height:30%"></div>
        </div>
      </div>
    </div>
  </div>
  <div class="aiva-feature__body">
    <span class="aiva-feature__label">Tertiary Analysis</span>
    <h2 class="aiva-feature__title">From raw variants to clinical insight</h2>
    <p class="aiva-feature__desc">Category-based analysis workflows, ACMG/AMP variant classification, and pharmacogenomics insights — structured to match clinical review standards.</p>
    <ul class="aiva-feature__bullets">
      <li>ACMG/AMP evidence-based variant scoring</li>
      <li>Pharmacogenomics (PGx) panel interpretation</li>
      <li>Analysis Hub with curated category cards</li>
      <li>Public classifier available without login</li>
    </ul>
    <a href="analysis/" class="aiva-feature__link">Explore Analysis →</a>
  </div>
</div>

<!-- FEATURE 4 – REPORTS (reversed) -->
<div class="aiva-feature aiva-feature--reverse">
  <div class="aiva-feature__visual">
    <div class="aiva-feature__mockup">
      <div class="aiva-mockup__bar">
        <span class="aiva-mockup__dot aiva-mockup__dot--red"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--yellow"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--green"></span>
        <span class="aiva-mockup__title">Clinical Report</span>
      </div>
      <div class="aiva-mockup__body">
        <div class="aiva-rpt__header">
          <div class="aiva-rpt__logo-block"></div>
          <div class="aiva-rpt__meta">
            <div class="aiva-rpt__line"></div>
            <div class="aiva-rpt__line aiva-rpt__line--short"></div>
          </div>
        </div>
        <div class="aiva-rpt__section">
          <div class="aiva-rpt__section-title">Interpretation</div>
          <div class="aiva-rpt__line"></div>
          <div class="aiva-rpt__line aiva-rpt__line--long"></div>
          <div class="aiva-rpt__line aiva-rpt__line--med"></div>
        </div>
        <div class="aiva-rpt__section">
          <div class="aiva-rpt__section-title">Findings</div>
          <div class="aiva-rpt__finding">
            <span class="aiva-badge aiva-badge--path">Pathogenic</span>
            <div class="aiva-rpt__line aiva-rpt__line--find"></div>
          </div>
          <div class="aiva-rpt__finding">
            <span class="aiva-badge aiva-badge--vus">VUS</span>
            <div class="aiva-rpt__line aiva-rpt__line--find"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="aiva-feature__body">
    <span class="aiva-feature__label">Reports</span>
    <h2 class="aiva-feature__title">Clinical reports in minutes, not hours</h2>
    <p class="aiva-feature__desc">AI-assisted auto-fill populates report sections from your variant data and analysis findings. Customizable templates, sample linking, and one-click export.</p>
    <ul class="aiva-feature__bullets">
      <li>AI Auto-Fill drafts interpretations automatically</li>
      <li>Link multiple samples to a single report</li>
      <li>Custom report templates per assay type</li>
      <li>Export to PDF or Word-compatible formats</li>
    </ul>
    <a href="reports/" class="aiva-feature__link">Explore Reports →</a>
  </div>
</div>

<!-- CAPABILITIES GRID -->
<div class="aiva-section">
  <span class="aiva-section__label">Full Platform</span>
  <h2 class="aiva-section__title">Everything you need, nothing you don't</h2>
  <p class="aiva-section__desc">Every module works together — no stitching tools, no manual data handoff.</p>
  <div class="aiva-cards">
    <a href="samples/" class="aiva-card">
      <span class="aiva-card__icon aiva-icon--upload"></span>
      <span class="aiva-card__title">Samples &amp; Uploads</span>
      <span class="aiva-card__desc">Drag-and-drop or cloud URL uploads with optional VEP and AnnotSV annotation.</span>
    </a>
    <a href="collaboration/" class="aiva-card">
      <span class="aiva-card__icon aiva-icon--collab"></span>
      <span class="aiva-card__title">Collaboration</span>
      <span class="aiva-card__desc">Projects, role-based access, variant flagging, and threaded comments.</span>
    </a>
    <a href="playbooks/" class="aiva-card">
      <span class="aiva-card__icon aiva-icon--book"></span>
      <span class="aiva-card__title">Playbooks</span>
      <span class="aiva-card__desc">Reusable analysis workflows you can share across your team or institution.</span>
    </a>
    <a href="api/" class="aiva-card">
      <span class="aiva-card__icon aiva-icon--api"></span>
      <span class="aiva-card__title">REST API</span>
      <span class="aiva-card__desc">Programmatic access for uploads, chat, classification, exports, and MCP.</span>
    </a>
    <a href="compliance/hipaa/" class="aiva-card">
      <span class="aiva-card__icon aiva-icon--shield"></span>
      <span class="aiva-card__title">HIPAA Compliance</span>
      <span class="aiva-card__desc">PHI detection, full audit trail, and enterprise-grade data security.</span>
    </a>
    <a href="admin/" class="aiva-card">
      <span class="aiva-card__icon aiva-icon--admin"></span>
      <span class="aiva-card__title">Administration</span>
      <span class="aiva-card__desc">User management, announcements, and org-level configuration.</span>
    </a>
  </div>
</div>

<!-- AUDIENCE -->
<div class="aiva-section">
  <span class="aiva-section__label">Built for Genomics Teams</span>
  <h2 class="aiva-section__title">Designed for every role in the workflow</h2>
  <div class="aiva-audience">
    <div class="aiva-audience__card">
      <div class="aiva-audience__role">Clinical Geneticists</div>
      <p class="aiva-audience__desc">Triage variants, apply ACMG/AMP criteria, and generate diagnostic reports with AI-assisted drafting.</p>
    </div>
    <div class="aiva-audience__card">
      <div class="aiva-audience__role">Research Scientists</div>
      <p class="aiva-audience__desc">Explore large WGS/WES datasets, search literature, and build custom analysis scripts with the code interpreter.</p>
    </div>
    <div class="aiva-audience__card">
      <div class="aiva-audience__role">Bioinformaticians</div>
      <p class="aiva-audience__desc">Integrate AIVA into automated pipelines via the REST API and MCP server for seamless data flow.</p>
    </div>
    <div class="aiva-audience__card">
      <div class="aiva-audience__role">Lab Directors</div>
      <p class="aiva-audience__desc">Manage multi-user projects with role-based access control, audit trails, and HIPAA-compliant infrastructure.</p>
    </div>
  </div>
</div>

<!-- QUICK LINKS -->
<div class="aiva-section">
  <span class="aiva-section__label">Quick Access</span>
  <h2 class="aiva-section__title">Popular starting points</h2>
  <div class="aiva-quicklinks">
    <a href="getting-started/account-setup/" class="aiva-quicklink">
      <div class="aiva-quicklink__inner">
        <span class="aiva-quicklink__title">Account Setup</span>
        <span class="aiva-quicklink__desc">Sign up, verify your email, and configure your profile</span>
      </div>
      <span class="aiva-quicklink__arrow">→</span>
    </a>
    <a href="getting-started/uploading-your-first-sample/" class="aiva-quicklink">
      <div class="aiva-quicklink__inner">
        <span class="aiva-quicklink__title">Your First Sample</span>
        <span class="aiva-quicklink__desc">End-to-end walkthrough from file selection to data table</span>
      </div>
      <span class="aiva-quicklink__arrow">→</span>
    </a>
    <a href="getting-started/subscription-tiers/" class="aiva-quicklink">
      <div class="aiva-quicklink__inner">
        <span class="aiva-quicklink__title">Subscription Tiers</span>
        <span class="aiva-quicklink__desc">Compare Free, Trial, Plus, and Pro plans</span>
      </div>
      <span class="aiva-quicklink__arrow">→</span>
    </a>
    <a href="aiva-chat/ai-tools/" class="aiva-quicklink">
      <div class="aiva-quicklink__inner">
        <span class="aiva-quicklink__title">AI Tools Reference</span>
        <span class="aiva-quicklink__desc">Full list of tools available to the AIVA assistant</span>
      </div>
      <span class="aiva-quicklink__arrow">→</span>
    </a>
    <a href="classification/" class="aiva-quicklink">
      <div class="aiva-quicklink__inner">
        <span class="aiva-quicklink__title">Variant Classifier</span>
        <span class="aiva-quicklink__desc">Public ACMG/AMP variant classification tool — no login needed</span>
      </div>
      <span class="aiva-quicklink__arrow">→</span>
    </a>
    <a href="compliance/hipaa/" class="aiva-quicklink">
      <div class="aiva-quicklink__inner">
        <span class="aiva-quicklink__title">HIPAA Compliance</span>
        <span class="aiva-quicklink__desc">PHI detection, audit trails, and data security</span>
      </div>
      <span class="aiva-quicklink__arrow">→</span>
    </a>
    <a href="api/" class="aiva-quicklink">
      <div class="aiva-quicklink__inner">
        <span class="aiva-quicklink__title">REST API</span>
        <span class="aiva-quicklink__desc">Programmatic access for uploads, chat, exports, and MCP</span>
      </div>
      <span class="aiva-quicklink__arrow">→</span>
    </a>
    <a href="faq/" class="aiva-quicklink">
      <div class="aiva-quicklink__inner">
        <span class="aiva-quicklink__title">FAQ</span>
        <span class="aiva-quicklink__desc">Answers to common questions</span>
      </div>
      <span class="aiva-quicklink__arrow">→</span>
    </a>
  </div>
</div>

<!-- CTA BANNER -->
<div class="aiva-cta">
  <h2>Ready to analyze your first sample?</h2>
  <p>Upload a VCF in seconds and let AIVA do the heavy lifting — annotation, analysis, and reporting all in one place.</p>
  <div class="aiva-hero__actions">
    <a href="getting-started/uploading-your-first-sample/" class="aiva-btn aiva-btn--primary">Upload Your First Sample →</a>
    <a href="faq/" class="aiva-btn aiva-btn--ghost">Read the FAQ</a>
  </div>
</div>
