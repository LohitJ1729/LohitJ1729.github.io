{{ define "main" }}

<style>
.container {
  max-width: 900px;
  margin: auto;
  padding: 20px;
}

/* HERO */
.hero {
  display: flex;
  align-items: center;
  gap: 30px;
  margin-top: 40px;
}

.hero-text h1 {
  font-size: 2.5em;
  margin-bottom: 5px;
}

.hero-text p {
  color: gray;
  font-size: 1.1em;
}

/* SECTION */
.section {
  margin-top: 50px;
}

.section h2 {
  border-bottom: 1px solid #ddd;
  padding-bottom: 5px;
}

/* CARDS */
.card {
  border: 1px solid #e5e5e5;
  border-radius: 10px;
  padding: 15px;
  margin-top: 15px;
  transition: 0.2s;
}

.card:hover {
  box-shadow: 0px 4px 12px rgba(0,0,0,0.08);
}

.card-title {
  font-weight: bold;
  font-size: 1.1em;
}

.card-meta {
  font-size: 0.85em;
  color: gray;
}

/* GRID */
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 15px;
}

@media (max-width: 700px) {
  .grid {
    grid-template-columns: 1fr;
  }
}
</style>

<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-text">
      <h1>Lohit J</h1>
      <p>Mathematics • Graphics • Miscellaneous</p>
      <p>
        I'm a PhD student at the Courant Institute of Mathematical Sciences at NYU. My area of focus is computer graphics. This site documents my learning and projects.
      </p>
      <p>
        <a href="https://github.com/LohitJ1729">GitHub</a> |
        <a href="https://www.linkedin.com/in/lohitjagarapu">LinkedIn</a> |
        <a href="https://www.lohitjagarapu.com/">Website</a>
      </p>
    </div>
  </div>

  <!-- RESEARCH INTERESTS -->
  <div class="section">
    <h2>Research Interests</h2>
    <p>
      My interests are broad ranging, from graphics to topology to mathematical physics. What unites all of them is math - it was what I studied in undergrad, and the lens I use to understand new concepts. As I read different articles and learn new topics, I will post them here with a distinctly math-y flavor.
    </p>
  </div>

  <!-- WRITING -->
  <div class="section">
    <h2>Writing</h2>

    {{ range first 5 (where .Site.RegularPages "Section" "posts") }}
      <div class="card">
        <div class="card-title">
          <a href="{{ .RelPermalink }}">{{ .Title }}</a>
        </div>
        <div class="card-meta">
          {{ .Date.Format "Jan 2, 2006" }}
        </div>
      </div>
    {{ end }}
  </div>

  <!-- PROJECTS -->
  <div class="section">
    <h2>Projects</h2>

    <div class="grid">
      {{ range where .Site.RegularPages "Section" "projects" }}
        <div class="card">
          <div class="card-title">
            <a href="{{ .RelPermalink }}">{{ .Title }}</a>
          </div>
          <div class="card-meta">
            {{ .Summary }}
          </div>
        </div>
      {{ end }}
    </div>
  </div>

  <!-- FEATURED DEMOS
  <div class="section">
    <h2>Interactive Demos</h2>
    <p>Fourier series approximation of a square wave:</p>

    <iframe src="/plots/fourier.html"
            style="width:100%; height:500px; border:1px solid #ddd; border-radius:10px;">
    </iframe>
  </div> -->

</div>

{{ end }}