<script>
  let vitaminCCurrent = $state(70);
  let vitaminCTotal = $state(90);

  let ironCurrent = $state(12);
  let ironTotal = $state(18);

  let vitaminDCurrent = $state(600);
  let vitaminDTotal = $state(800);

  let calciumCurrent = $state(800);
  let calciumTotal = $state(1000);

  const calculatePercentage = (current, total) => {
    const percentage = (current / total) * 100;
    return Math.max(0, Math.min(100, percentage));
  };

  let vitaminCPercentage = $derived(
    calculatePercentage(vitaminCCurrent, vitaminCTotal)
  );
  let ironPercentage = $derived(calculatePercentage(ironCurrent, ironTotal));
  let vitaminDPercentage = $derived(
    calculatePercentage(vitaminDCurrent, vitaminDTotal)
  );
  let calciumPercentage = $derived(
    calculatePercentage(calciumCurrent, calciumTotal)
  );

  const formatMicroText = (current, total, unit) => {
    return `${current}${unit} / ${total}${unit}`;
  };

  const getFilledSquares = (percentage) => {
    return Math.floor(percentage / 10);
  };
</script>

<div class="micro-card-container">
  <div class="micro-card">
    <h2 class="micro-title">Minerals</h2>

    <div class="micro-item-grid">
      <div class="micro-item">
        <div class="micro-header">
          <h3 class="micro-subtitle">Vitamin C</h3>
          <span class="micro-value"
            >{formatMicroText(vitaminCCurrent, vitaminCTotal, "mg")}</span
          >
        </div>
        <div class="progress-square-bar-wrapper">
          {#each Array(10) as _, i}
            <div
              class="progress-square-segment"
              class:filled={i < getFilledSquares(vitaminCPercentage)}
            ></div>
          {/each}
        </div>
      </div>

      <div class="micro-item">
        <div class="micro-header">
          <h3 class="micro-subtitle">Iron</h3>
          <span class="micro-value"
            >{formatMicroText(ironCurrent, ironTotal, "mg")}</span
          >
        </div>
        <div class="progress-square-bar-wrapper">
          {#each Array(10) as _, i}
            <div
              class="progress-square-segment"
              class:filled={i < getFilledSquares(ironPercentage)}
            ></div>
          {/each}
        </div>
      </div>

      <div class="micro-item">
        <div class="micro-header">
          <h3 class="micro-subtitle">Vitamin D</h3>
          <span class="micro-value"
            >{formatMicroText(vitaminDCurrent, vitaminDTotal, "IU")}</span
          >
        </div>
        <div class="progress-square-bar-wrapper">
          {#each Array(10) as _, i}
            <div
              class="progress-square-segment"
              class:filled={i < getFilledSquares(vitaminDPercentage)}
            ></div>
          {/each}
        </div>
      </div>

      <div class="micro-item">
        <div class="micro-header">
          <h3 class="micro-subtitle">Calcium</h3>
          <span class="micro-value"
            >{formatMicroText(calciumCurrent, calciumTotal, "mg")}</span
          >
        </div>
        <div class="progress-square-bar-wrapper">
          {#each Array(10) as _, i}
            <div
              class="progress-square-segment"
              class:filled={i < getFilledSquares(calciumPercentage)}
            ></div>
          {/each}
        </div>
      </div>
    </div>
  </div>
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
  }

  .micro-card-container {
    min-height: 400px;
    background-color: #f3f4f6;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
  }

  @media (min-width: 640px) {
    .micro-card-container {
      padding: 1.5rem;
    }
  }
  @media (min-width: 1024px) {
    .micro-card-container {
      padding: 2rem;
    }
  }

  .micro-card {
    background-color: #ffffff;
    border-radius: 0;
    box-shadow:
      0 20px 25px -5px rgba(0, 0, 0, 0.1),
      0 10px 10px -5px rgba(0, 0, 0, 0.04);
    padding: 1.5rem;
    width: 100%;
    max-width: 28rem;
  }

  .micro-title {
    font-size: 2.25rem;
    font-weight: 700;
    color: #1f2937;
    line-height: 1;
    margin-bottom: 1.5rem;
    text-align: left;
  }

  .micro-item-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1.25rem;
  }

  .micro-item {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  .micro-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    margin-bottom: 0.25rem;
  }

  .micro-subtitle {
    font-size: 1.1rem;
    font-weight: 700;
    color: #374151;
    text-align: left;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    flex-shrink: 1;
    min-width: 0;
  }

  .progress-square-bar-wrapper {
    display: flex;
    gap: 0.15rem;
    width: 100%;
    height: 1rem;
  }

  .progress-square-segment {
    flex-grow: 1;
    height: 100%;
    background-color: #e5e7eb;
    border: 1px solid #d1d5db;
    flex-shrink: 0;
  }

  .progress-square-segment.filled {
    background-color: #4ade80;
    border-color: #4ade80;
  }

  .micro-value {
    font-size: 0.95rem;
    font-weight: 400;
    color: #6b7280;
    white-space: nowrap;
    text-align: right;
    flex-shrink: 0;
    margin-left: 0.5rem;
  }
</style>
