<script>
  let emoji = "✅";
  let percentage = 84;
  let description = "Follow Through Performance";
</script>

<div class="container">
  <div class="progress-card">
    <div class="emoji-container">
      {emoji}
    </div>
    <div class="text-content">
      <div class="percentage">{percentage}%</div>
      <div class="description">{description}</div>
    </div>
  </div>
</div>

<style>
  .container {
    display: flex;
    justify-items: center;
    align-items: center;
    background-color: #f3f4f6;
    min-height: 200px;
  }

  .progress-card {
    font-family: Arial, sans-serif;
    display: flex;
    flex-direction: row-reverse;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    background-color: white;
    border-radius: 0;
    padding: 1rem;
    margin: 0 auto;
    box-shadow:
      0 2px 4px rgba(0, 0, 0, 0.04),
      0 4px 6px rgba(0, 0, 0, 0.05);
    max-width: 20rem;
    box-sizing: border-box;
  }

  .emoji-container {
    width: 2.75rem;
    height: 2.75rem;
    border-radius: 9999px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.5rem;
    margin-left: 1rem;
    background-color: white;
    flex-shrink: 0;
  }

  .text-content {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    text-align: left;
  }

  .percentage {
    font-size: 1.75rem;
    font-weight: 700;
    color: black;
    line-height: 1;
  }

  .description {
    font-size: 0.875rem;
    color: black;
    font-weight: 500;
    margin-top: 0.25rem;
  }
</style>
