<script>
  let proteinCurrent = $state(40);
  let proteinTotal = $state(90);

  let carbsCurrent = $state(180);
  let carbsTotal = $state(300);

  let unsaturatedFatCurrent = $state(25);
  let unsaturatedFatTotal = $state(40);

  let saturatedFatCurrent = $state(10);
  let saturatedFatTotal = $state(20);

  const calculatePercentage = (current, total) => {
    const percentage = (current / total) * 100;
    return Math.max(0, Math.min(100, percentage));
  };

  let proteinPercentage = $derived(
    calculatePercentage(proteinCurrent, proteinTotal)
  );
  let carbsPercentage = $derived(calculatePercentage(carbsCurrent, carbsTotal));
  let unsaturatedFatPercentage = $derived(
    calculatePercentage(unsaturatedFatCurrent, unsaturatedFatTotal)
  );
  let saturatedFatPercentage = $derived(
    calculatePercentage(saturatedFatCurrent, saturatedFatTotal)
  );

  const formatMacroText = (current, total) => {
    return `${current}g / ${total}g`;
  };

  const getPercentageColor = (percentage) => {
    if (percentage > 75) {
      return "#22c55e";
    } else if (percentage > 50) {
      return "#4ade80";
    } else if (percentage > 25) {
      return "#86efac";
    } else if (percentage > 0) {
      return "#dcfce7";
    } else {
      return "#e5e7eb";
    }
  };
</script>

<div class="banner-card-container">
  <div class="banner-card">
    <h2 class="banner-title">Macronutrients</h2>

    <div class="macro-grid">
      <div
        class="macro-square-block"
        style="background-color: {getPercentageColor(
          proteinPercentage
        )}; border: 1px solid {getPercentageColor(proteinPercentage)};"
      >
        <h3 class="macro-subtitle">Protein</h3>
        <span class="macro-value"
          >{formatMacroText(proteinCurrent, proteinTotal)}</span
        >
      </div>

      <div
        class="macro-square-block"
        style="background-color: {getPercentageColor(
          carbsPercentage
        )}; border: 1px solid {getPercentageColor(carbsPercentage)};"
      >
        <h3 class="macro-subtitle">Carbs</h3>
        <span class="macro-value"
          >{formatMacroText(carbsCurrent, carbsTotal)}</span
        >
      </div>

      <div
        class="macro-square-block"
        style="background-color: {getPercentageColor(
          unsaturatedFatPercentage
        )}; border: 1px solid {getPercentageColor(unsaturatedFatPercentage)};"
      >
        <h3 class="macro-subtitle">Unsaturated Fat</h3>
        <span class="macro-value"
          >{formatMacroText(unsaturatedFatCurrent, unsaturatedFatTotal)}</span
        >
      </div>

      <div
        class="macro-square-block"
        style="background-color: {getPercentageColor(
          saturatedFatPercentage
        )}; border: 1px solid {getPercentageColor(saturatedFatPercentage)};"
      >
        <h3 class="macro-subtitle">Saturated Fat</h3>
        <span class="macro-value"
          >{formatMacroText(saturatedFatCurrent, saturatedFatTotal)}</span
        >
      </div>
    </div>

    <div class="color-guide">
      <h3 class="guide-title">Daily Intake Progress</h3>
      <div class="guide-items">
        <div class="guide-item">
          <span class="guide-color-box" style="background-color: #dcfce7;"
          ></span>
          <span class="guide-text">0-25%</span>
        </div>
        <div class="guide-item">
          <span class="guide-color-box" style="background-color: #86efac;"
          ></span>
          <span class="guide-text">26-50%</span>
        </div>
        <div class="guide-item">
          <span class="guide-color-box" style="background-color: #4ade80;"
          ></span>
          <span class="guide-text">51-75%</span>
        </div>
        <div class="guide-item">
          <span class="guide-color-box" style="background-color: #22c55e;"
          ></span>
          <span class="guide-text">76-100%</span>
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

  .banner-card-container {
    min-height: 100vh;
    background-color: #f3f4f6;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
  }

  @media (min-width: 640px) {
    .banner-card-container {
      padding: 1.5rem;
    }
  }

  @media (min-width: 1024px) {
    .banner-card-container {
      padding: 2rem;
    }
  }

  .banner-card {
    background-color: #ffffff;
    border-radius: 0;
    box-shadow:
      0 20px 25px -5px rgba(0, 0, 0, 0.1),
      0 10px 10px -5px rgba(0, 0, 0, 0.04);
    padding: 1.5rem;
    width: 100%;
    max-width: 20rem;
  }

  @media (min-width: 640px) {
    .banner-card {
      max-width: 28rem;
    }
  }

  .banner-title {
    font-size: 2.25rem;
    font-weight: 700;
    color: #1f2937;
    line-height: 1;
    margin-bottom: 1.5rem;
    text-align: left;
  }

  .macro-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.75rem;
    margin-bottom: 1.5rem;
  }

  .macro-square-block {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    padding: 0.5rem;
    aspect-ratio: 1 / 1;
    min-height: 5rem;
    transition:
      background-color 0.3s ease-in-out,
      border-color 0.3s ease-in-out;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
    color: #1f2937;
  }

  .macro-subtitle {
    font-size: 0.9rem;
    font-weight: 700;
    margin-bottom: 0.15rem;
    text-align: left;
    line-height: 1.2;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    width: 100%;
  }

  .macro-value {
    font-size: 0.75rem;
    font-weight: 400;
    text-align: left;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    width: 100%;
  }

  .color-guide {
    margin-top: 1.5rem;
    padding-top: 1rem;
    border-top: 1px solid #e5e7eb;
  }

  .guide-title {
    font-size: 1rem;
    font-weight: 700;
    color: #1f2937;
    margin-bottom: 0.75rem;
    text-align: left;
  }

  .guide-items {
    display: flex;
    flex-wrap: wrap;
    gap: 0.75rem;
    justify-content: flex-start;
  }

  .guide-item {
    display: flex;
    align-items: center;
    gap: 0.4rem;
  }

  .guide-color-box {
    width: 1rem;
    height: 1rem;
    border: 1px solid rgba(0, 0, 0, 0.1);
    flex-shrink: 0;
  }

  .guide-text {
    font-size: 0.85rem;
    color: #4b5563;
    white-space: nowrap;
  }
</style>
