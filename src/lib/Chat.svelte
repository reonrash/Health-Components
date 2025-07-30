<script>
  let mealInput = $state("");

  const sendMeal = () => {
    if (mealInput.trim()) {
      console.log("Meal tracked:", mealInput);
      alert("Meal tracked: " + mealInput);
      mealInput = "";
    } else {
      alert("Please enter a meal description.");
    }
  };
</script>

<div class="meal-tracker-container">
  <div class="meal-tracker-card">
    <h2 class="meal-tracker-title">Good Morning, Alex!</h2>

    <p class="meal-tracker-subtitle">
      Please describe the meal(s) you had today and we will add it to your
      tracker.
    </p>

    <textarea
      placeholder="e.g., Chicken salad, rice, and beans"
      class="meal-input-standalone"
      bind:value={mealInput}
      rows="2"
      onkeydown={(e) => {
        if (e.key === "Enter" && !e.shiftKey) {
          e.preventDefault();
          sendMeal();
        }
      }}
    ></textarea>
    <button class="send-button-standalone" onclick={sendMeal}> Send </button>
  </div>
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
  }

  .meal-tracker-container {
    min-height: 400px;
    background-color: #f3f4f6;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
  }

  @media (min-width: 640px) {
    .meal-tracker-container {
      padding: 1.5rem;
    }
  }

  @media (min-width: 1024px) {
    .meal-tracker-container {
      padding: 2rem;
    }
  }

  .meal-tracker-card {
    background-color: #ffffff;
    border-radius: 0;
    box-shadow:
      0 20px 25px -5px rgba(0, 0, 0, 0.1),
      0 10px 10px -5px rgba(0, 0, 0, 0.04);
    padding: 1.5rem;
    width: 100%;
    max-width: 35rem;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  .meal-tracker-title {
    font-size: 2.25rem;
    font-weight: 700;
    color: #1f2937;
    line-height: 1;
    margin-bottom: 1rem;
    text-align: left;
  }

  .meal-tracker-subtitle {
    font-size: 1rem;
    font-weight: 400;
    color: #4b5563;
    margin-bottom: 1.5rem;
    text-align: left;
    line-height: 1.5;
  }

  .meal-input-standalone {
    width: 100%;
    padding: 1rem 1.25rem;
    font-size: 1.1rem;
    border: 1px solid #d1d5db;
    outline: none;
    background-color: #ffffff;
    color: #1f2937;
    margin-bottom: 1rem;
    resize: vertical;
    min-height: 4rem;
  }

  .meal-input-standalone::placeholder {
    color: #9ca3af;
  }

  .send-button-standalone {
    background-color: #4ade80;
    color: #ffffff;
    font-size: 1rem;
    font-weight: 600;
    padding: 0.75rem 1.25rem;
    border: none;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
    width: 100%;
    text-align: center;
  }

  .send-button-standalone:hover {
    background-color: #22c55e;
  }

  .send-button-standalone:active {
    background-color: #16a34a;
  }
</style>
