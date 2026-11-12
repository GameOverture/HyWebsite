---
title: " "
hide:
  - title
  - toc
  - navigation
---

<style>
.features-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(320px, 1fr));
  gap: 1.5rem;
  margin: 2rem 0;
}

@media (max-width: 700px) {
  .features-grid {
    grid-template-columns: 1fr;
  }
}

.feature-card {
  border: 1px solid var(--md-default-fg-color--lighter);
  border-radius: 8px;
  padding: 1.2rem 1.5rem;
  background: var(--md-code-bg-color);
  box-shadow: var(--md-shadow-z1);
}

.feature-card h3 {
  margin-top: 0;
  text-align: center;
}

.feature-card p {
  font-size: 0.65rem;
  line-height: 1.35rem;
  margin-bottom: 0.8rem; /* Reduce space below paragraph */
}

.center-buttons {
  text-align: center;
  margin: 0.8rem 0 0.2rem 0; /* Reduced vertical spacing */
}

.center-buttons a {
  display: inline-block;
  margin: 0 0.4rem;
  padding: 0.6rem 1.2rem;
  background: var(--md-primary-fg-color);
  color: white;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
}

.center-buttons a:hover {
  background: var(--md-primary-fg-color--light);
}

.center { text-align: center; }
</style>

<p class="center">
    <center><h1>Welcome to the official documentation for <a href="https://hyengine.org"><strong>Harmony Engine</strong></a>!</h1></center>
<p class="center">
    New to Harmony? Get step-by-step instructions for installing Harmony Engine and creating your first functional project.
    <div class="center-buttons">
	    <a href="getting-started/">Getting Started</a>
    </div>
</p>
</p>

<div class="features-grid">

  <div class="feature-card">
    <h3><b style="color: #FA5A0A;">HyEditor</b></h3>
    <p class="center">
      Visually create Prefabs which are the building blocks of your game. All of Harmony's tools are wrapped into HyEditor to handle project & build management, the asset pipeline, and creating Prefabs and Entities.
    </p>
	<div class="center-buttons">
	  <a href="editor/">Editor Manual</a>
	</div>
  </div>

  <div class="feature-card">
    <h3><b style="color: #FA5A0A;">HyEngine</b></h3>
    <p class="center">
      Programming with Harmony’s runtime API and how it works under the hood. Integrate your game's logic with Prefab node instances, and setup windows, cameras, input, rendering, and more.
    </p>
	<div class="center-buttons">
	  <a href="programming/">Programming Manual</a>
	</div>
  </div>

</div>

<center>
    <h3>Learn with Sample Projects</h3>
    Browse a collection of sample projects demonstrating major features how they work in practice. Each example illustrates practical usage patterns.
    <div class="center-buttons">
	    <a href="examples/">Example Projects</a>
    </div>
</center>
