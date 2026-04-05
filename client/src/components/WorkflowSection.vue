<template>
  <section id="workflow" class="section-dark sec-pad">
    <div class="workflow-inner">
      <h2 class="sec-title">Workflow</h2>
      <div class="divider"></div>
      <img
        src="/images/workflow.jpg"
        alt="SAVVY System Workflow"
        class="workflow-img"
      />
      <p class="workflow-caption">
        <strong>The workflow of SAVVY:</strong> (A) brain data acquisition and pre-processing,
        (B) attention modeling framework with a fusion module, a DDQN-based quantification model (B1),
        and an attention decomposition module, (C) course structure and information density extraction.
        These outputs feed into the three visualization modules of SAVVY.
      </p>
    </div>
  </section>
</template>

<style scoped>
.workflow-inner {
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

.workflow-img {
  width: 100%;
  display: block;
  border-radius: 12px;
  box-shadow: 0 4px 24px rgba(0,0,0,.35);
}

.workflow-caption {
  font-family: Arial, sans-serif;
  font-size: 15px;
  color: var(--muted);
  line-height: 1.8;
  margin-top: 1.4rem;
  text-align: left;
}

.workflow-caption strong {
  color: var(--text);
}
</style>
