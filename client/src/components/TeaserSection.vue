<template>
  <section id="teaser" class="section-dark sec-pad">
    <div class="teaser-inner">
      <h2 class="sec-title">Interface</h2>
      <div class="divider"></div>
      <img
        src="/images/teaser.jpg"
        alt="Interface: Overview of the SAVVY system"
        class="teaser-img"
      />
      <p class="teaser-caption">
        <strong>Interface:</strong> The interface of SAVVY consists of the Concept Module (A), the Group Module (B),
        and the Individual Module (C). The Concept Module (A) presents the course content structure and detailed
        information of each concept (A1). The Group Module (B) displays temporal trends of group attention and
        detailed audiovisual information, where the video annotation panel (B1) further assists teachers in locating
        and annotating video segments that require revision. The Individual Module (C) provides attention change
        trajectories for each student (C1) to verify findings during the exploration process.
      </p>
    </div>
  </section>
</template>

<style scoped>
.teaser-inner {
  max-width: 1100px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-left: clamp(16px, 4vw, 40px);
  padding-right: clamp(16px, 4vw, 40px);
}

.sec-title {
  font-family: Arial, sans-serif;
  font-size: 28.8px;
  font-weight: 700;
  color: var(--text);
  text-align: center;
  margin-bottom: 12px;
}

.teaser-img {
  width: 100%;
  display: block;
  border-radius: 12px;
  box-shadow: 0 4px 24px rgba(0,0,0,.35);
}

.teaser-caption {
  font-family: Arial, sans-serif;
  font-size: 15px;
  color: var(--muted);
  line-height: 1.8;
  margin-top: 1.4rem;
  text-align: left;
}

.teaser-caption strong {
  color: var(--text);
}
</style>
