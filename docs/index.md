---
title: AIVA – Whole Genome Interpretation in Minutes
description: Documentation for AIVA - your AI Clinical Analyst for whole genome interpretation, variant classification, and clinical reporting
hide:
  - navigation
  - toc
---

# Whole Genome Interpretation in Minutes, Not Weeks

AIVA is your AI Clinical Analyst. Go from FASTQ to a finalized clinical report in under 1 hour, or drop a VCF and have classified, annotated results in approximately 5 minutes. AIVA automates variant annotation, ACMG/AMP classification, literature review, and report generation -- delivering 90%+ pathogenic sensitivity in a single platform built for clinical-grade genomics.

---

<!-- FEATURES HEADER -->
<div class="aiva-section" style="text-align:center;">
  <h2 class="aiva-section__title" style="border:none;">From sample to signed report</h2>
</div>

<!-- FEATURE 1 – SECONDARY ANALYSIS -->
<div class="aiva-feature">
  <div class="aiva-feature__visual">
    <div class="aiva-feature__mockup">
      <div class="aiva-mockup__bar">
        <span class="aiva-mockup__dot aiva-mockup__dot--red"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--yellow"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--green"></span>
        <span class="aiva-mockup__title">Pipeline</span>
      </div>
      <div class="aiva-mockup__body">
        <div class="aiva-flow">
          <svg class="aiva-flow__svg" viewBox="0 0 340 280" fill="none" xmlns="http://www.w3.org/2000/svg">
            <!-- Connector lines -->
            <g stroke="rgba(0,188,212,.35)" stroke-width="1.5" fill="none">
              <!-- FASTQ → Variant Calling -->
              <line x1="100" y1="36" x2="100" y2="68"/>
              <!-- Variant Calling → BAM -->
              <line x1="100" y1="98" x2="100" y2="128"/>
              <!-- BAM → PGx (straight down) -->
              <line x1="80" y1="158" x2="80" y2="196"/>
              <!-- BAM → Annotation (right branch) -->
              <path d="M120,158 L120,168 L235,168 L235,196"/>
              <!-- VCF → Annotation (straight down, merges) -->
              <line x1="260" y1="36" x2="260" y2="168"/>
              <line x1="260" y1="168" x2="235" y2="168"/>
            </g>
            <!-- Arrowheads (all pointing down) -->
            <g fill="rgba(0,188,212,.4)">
              <polygon points="96,64 100,72 104,64"/>
              <polygon points="96,124 100,132 104,124"/>
              <polygon points="76,190 80,198 84,190"/>
              <polygon points="231,190 235,198 239,190"/>
            </g>
            <!-- Step boxes -->
            <g>
              <!-- FASTQ -->
              <rect x="35" y="6" width="130" height="30" rx="6" fill="rgba(0,188,212,.08)" stroke="rgba(0,188,212,.3)"/>
              <text x="100" y="26" text-anchor="middle" fill="currentColor" font-size="12" font-weight="600">FASTQ</text>
              <!-- Variant Calling -->
              <rect x="25" y="68" width="150" height="30" rx="6" fill="rgba(0,188,212,.08)" stroke="rgba(0,188,212,.3)"/>
              <text x="100" y="88" text-anchor="middle" fill="currentColor" font-size="12" font-weight="600">Variant Calling</text>
              <!-- BAM -->
              <rect x="35" y="128" width="130" height="30" rx="6" fill="rgba(0,188,212,.08)" stroke="rgba(0,188,212,.3)"/>
              <text x="100" y="148" text-anchor="middle" fill="currentColor" font-size="12" font-weight="600">BAM</text>
              <!-- PGx -->
              <rect x="20" y="196" width="120" height="30" rx="6" fill="rgba(0,150,136,.12)" stroke="rgba(0,150,136,.4)"/>
              <text x="80" y="216" text-anchor="middle" fill="currentColor" font-size="12" font-weight="600">PGx</text>
              <!-- Annotation -->
              <rect x="170" y="196" width="130" height="30" rx="6" fill="rgba(0,150,136,.12)" stroke="rgba(0,150,136,.4)"/>
              <text x="235" y="216" text-anchor="middle" fill="currentColor" font-size="12" font-weight="600">Annotation</text>
              <!-- VCF -->
              <rect x="200" y="6" width="120" height="30" rx="6" fill="rgba(0,188,212,.08)" stroke="rgba(0,188,212,.3)"/>
              <text x="260" y="26" text-anchor="middle" fill="currentColor" font-size="12" font-weight="600">VCF</text>
            </g>
            <!-- Path labels -->
            <text x="80" y="270" text-anchor="middle" fill="currentColor" font-size="9" opacity=".4" font-weight="500" letter-spacing="1">GPU PIPELINE</text>
            <text x="260" y="270" text-anchor="middle" fill="currentColor" font-size="9" opacity=".4" font-weight="500" letter-spacing="1">DIRECT UPLOAD</text>
          </svg>
        </div>
      </div>
    </div>
  </div>
  <div class="aiva-feature__body">
    <span class="aiva-feature__label">Get Started</span>
    <h2 class="aiva-feature__title">Start from FASTQ or VCF.</h2>
    <p class="aiva-feature__desc">Upload raw sequencing data and let GPU-accelerated Parabricks pipelines call variants, generate BAMs, and assign PGx star alleles. Or skip the pipeline entirely -- drop a VCF (small or structural variants) and AIVA annotates it for analysis.</p>
    <ul class="aiva-feature__bullets">
      <li>Small variant calling powered by NVIDIA Parabricks on GPUs</li>
      <li>BAM file generation with direct IGV links for visual review</li>
      <li>Pharmacogenomic variant calling and star-allele assignment</li>
      <li>Automated annotation with ClinVar, gnomAD, and DITTO scoring</li>
    </ul>
    <a href="samples/" class="aiva-feature__link">Samples & Uploads →</a>
  </div>
</div>

<!-- FEATURE 2 – AIVA CHAT (reversed) -->
<div class="aiva-feature aiva-feature--reverse">
  <div class="aiva-feature__visual">
    <div class="aiva-feature__mockup">
      <div class="aiva-mockup__bar">
        <span class="aiva-mockup__dot aiva-mockup__dot--red"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--yellow"></span>
        <span class="aiva-mockup__dot aiva-mockup__dot--green"></span>
        <span class="aiva-mockup__title">AIVA Chat</span>
      </div>
      <div class="aiva-mockup__body">
        <div class="aiva-chat__msg aiva-chat__msg--user">List P/LP variants in @sample:patient007</div>
        <div class="aiva-chat__msg aiva-chat__msg--ai">
          <span class="aiva-chat__label">AIVA</span>
          Found 12 pathogenic variants. Showing top results by classification…
        </div>
        <table class="aiva-chat__table">
          <thead>
            <tr><th>Gene</th><th>Variant</th><th>Class</th></tr>
          </thead>
          <tbody>
            <tr><td>BRCA1</td><td>c.5266dupC (p.Gln1756fs)</td><td><span class="aiva-badge aiva-badge--path">Pathogenic</span></td></tr>
            <tr><td>TP53</td><td>c.718C>T (p.Gln240*)</td><td><span class="aiva-badge aiva-badge--path">Pathogenic</span></td></tr>
            <tr><td>MLH1</td><td>c.1972dupC (p.Gln658fs)</td><td><span class="aiva-badge aiva-badge--lpath">Likely Path.</span></td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
  <div class="aiva-feature__body">
    <span class="aiva-feature__label">AIVA Chat</span>
    <h2 class="aiva-feature__title">Your AI Clinical Analyst, not just an assistant</h2>
    <p class="aiva-feature__desc">AIVA Chat does the work a clinical analyst does in seconds instead of hours. Ask a question in plain English and get classified, evidence-backed answers grounded in your samples' data.</p>
    <ul class="aiva-feature__bullets">
      <li>Review and classify variants with a single prompt</li>
      <li>Automated literature review with cited evidence</li>
      <li>HPO-driven gene prioritization</li>
      <li>Knowledge graph associations between genes, diseases, drugs, etc.</li>
    </ul>
    <a href="aiva-chat/" class="aiva-feature__link">AIVA Chat →</a>
  </div>
</div>

<!-- FEATURE 3 – MANUAL ANALYSIS -->
<div class="aiva-feature">
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
          <span>Gene</span><span>HGVS</span><span>DITTO</span><span>Class</span>
        </div>
        <div class="aiva-tbl__row">
          <span>BRCA2</span><span>c.5946delT</span><span>0.97</span>
          <span class="aiva-badge aiva-badge--path">Path</span>
        </div>
        <div class="aiva-tbl__row aiva-tbl__row--alt">
          <span>PTEN</span><span>c.388C>T</span><span>0.91</span>
          <span class="aiva-badge aiva-badge--lpath">LP</span>
        </div>
        <div class="aiva-tbl__row">
          <span>APC</span><span>c.3920T>A</span><span>0.54</span>
          <span class="aiva-badge aiva-badge--vus">VUS</span>
        </div>
        <div class="aiva-tbl__row aiva-tbl__row--alt">
          <span>RB1</span><span>c.2117G>A</span><span>0.42</span>
          <span class="aiva-badge aiva-badge--vus">VUS</span>
        </div>
        <div class="aiva-tbl__foot">whole genome scale · real-time filtering</div>
      </div>
    </div>
  </div>
  <div class="aiva-feature__body">
    <span class="aiva-feature__label">Manual Analysis</span>
    <h2 class="aiva-feature__title">Prefer hands-on? Analyze variants yourself.</h2>
    <p class="aiva-feature__desc">Whole genome sequencing produces millions of variants per sample. Filter by gene, consequence, frequency, or ACMG class and see results in real time.</p>
    <ul class="aiva-feature__bullets">
      <li>Virtualized rendering with zero performance degradation</li>
      <li>One-click export of filtered views to CSV, TSV, or direct to report</li>
      <li>Per-variant flagging, comments, and threaded review for clinical sign-off</li>
    </ul>
    <a href="data-table/" class="aiva-feature__link">Data Table →</a>
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
      <li>Edit and refine auto-generated content</li>
      <li>Upload custom report templates per assay type</li>
      <li>Sign and export reports</li>
    </ul>
    <a href="reports/" class="aiva-feature__link">Reports →</a>
  </div>
</div>

---

<!-- CAPABILITIES GRID -->
<div class="aiva-section">
  <span class="aiva-section__label">Full Platform</span>
  <h2 class="aiva-section__title" style="border:none;">Everything you need in one platform</h2>
  <p class="aiva-section__desc">Every module works together — no stitching tools, no manual data handoff.</p>
  <div class="aiva-cards">
    <a href="samples/" class="aiva-card">
      <span class="aiva-card__title">Samples &amp; Uploads</span>
      <span class="aiva-card__desc">Drag-and-drop or cloud URL uploads with optional variant annotation.</span>
    </a>
    <a href="collaboration/" class="aiva-card">
      <span class="aiva-card__title">Collaboration</span>
      <span class="aiva-card__desc">Projects, role-based access, variant flagging, and threaded comments.</span>
    </a>
    <a href="playbooks/" class="aiva-card">
      <span class="aiva-card__title">Playbooks</span>
      <span class="aiva-card__desc">Reusable analysis workflows you can share across your team or institution.</span>
    </a>
    <a href="api/" class="aiva-card">
      <span class="aiva-card__title">REST API</span>
      <span class="aiva-card__desc">Programmatic access for uploads, chat, classification, exports, and MCP.</span>
    </a>
    <a href="compliance/hipaa/" class="aiva-card">
      <span class="aiva-card__title">HIPAA Compliance</span>
      <span class="aiva-card__desc">PHI detection, full audit trail, and enterprise-grade data security.</span>
    </a>
  </div>
</div>

---

<!-- AUDIENCE -->
<div class="aiva-section">
  <span class="aiva-section__label">Built for Genomics Teams</span>
  <h2 class="aiva-section__title" style="border:none;">Designed for every role in the workflow</h2>
  <div class="aiva-audience">
    <div class="aiva-audience__card">
      <div class="aiva-audience__role">Clinical Geneticists</div>
      <p class="aiva-audience__desc">Review variants, apply ACMG/AMP criteria, and generate diagnostic reports with AI-assisted drafting.</p>
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

---

<!-- QUICK LINKS -->
<div class="aiva-section">
  <span class="aiva-section__label">Quick Access</span>
  <h2 class="aiva-section__title" style="border:none;">Popular starting points</h2>
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
