<template>
  <section id="workflow" class="section-dark sec-pad">
    <div class="workflow-inner">
      <h2 class="section-title">Workflow</h2>
      <img
        src="/images/workflow.jpg"
        alt="SAVVY System Workflow"
        class="workflow-img"
      />
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
.section-title {
  font-family: Arial, sans-serif;
  font-size: clamp(1.4rem, 2.8vw, 1.8rem);
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 24px;
  text-align: left;
}
.workflow-img {
  width: 100%;
  display: block;
  border-radius: 12px;
  box-shadow: 0 4px 24px rgba(0,0,0,.35);
}
</style>
