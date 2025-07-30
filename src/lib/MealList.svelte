<script>
  let meals = $state([
    {
      id: 1,
      name: "Grilled Chicken Salad",
      labels: ["High Protein", "Low Carb"],
    },
    { id: 2, name: "Lentil Soup", labels: ["High Fiber", "Vegan"] },
    {
      id: 3,
      name: "Salmon with Asparagus",
      labels: ["Omega-3s", "High Protein"],
    },
    {
      id: 4,
      name: "Oatmeal with Berries",
      labels: ["Whole Grains", "Antioxidants"],
    },
  ]);

  const deleteMeal = (idToDelete) => {
    meals = meals.filter((meal) => meal.id !== idToDelete);
  };
</script>

<div class="meal-list-container">
  <div class="meal-list-card">
    <h2 class="list-title">Today's Meals</h2>

    {#if meals.length > 0}
      <div class="meal-items-wrapper">
        {#each meals as meal (meal.id)}
          <div class="meal-item-card">
            <div class="meal-details">
              <h3 class="meal-name">{meal.name}</h3>
              <div class="meal-labels">
                {#each meal.labels as label}
                  <span class="meal-label">{label}</span>
                {/each}
              </div>
            </div>
            <button class="delete-button" onclick={() => deleteMeal(meal.id)}>
              X
            </button>
          </div>
        {/each}
      </div>
    {:else}
      <p class="no-meals-message">No meals tracked yet today.</p>
    {/if}
  </div>
</div>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
  }

  .meal-list-container {
    min-height: 400px;
    background-color: #f3f4f6;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
  }

  @media (min-width: 640px) {
    .meal-list-container {
      padding: 1.5rem;
    }
  }

  @media (min-width: 1024px) {
    .meal-list-container {
      padding: 2rem;
    }
  }

  .meal-list-card {
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

  .list-title {
    font-size: 2.25rem;
    font-weight: 700;
    color: #1f2937;
    line-height: 1;
    margin-bottom: 1.5rem;
    text-align: left;
  }

  .meal-items-wrapper {
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  .meal-item-card {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #f9fafb;
    border: 1px solid #e5e7eb;
    padding: 0.75rem 1rem;
    border-radius: 0;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
  }

  .meal-details {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    flex-grow: 1;
    margin-right: 0.75rem;
  }

  .meal-name {
    font-size: 1rem;
    font-weight: 600;
    color: #1f2937;
    margin-bottom: 0.25rem;
    line-height: 1.2;
  }

  .meal-labels {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }

  .meal-label {
    font-size: 0.75rem;
    font-weight: 500;
    color: #4b5563;
    background-color: #e0e7ff;
    padding: 0.2rem 0.5rem;
    border-radius: 0;
    white-space: nowrap;
  }

  .delete-button {
    background-color: #ef4444;
    color: #ffffff;
    font-size: 0.85rem;
    font-weight: 700;
    width: 1.75rem;
    height: 1.75rem;
    border: none;
    cursor: pointer;
    transition: background-color 0.2s ease-in-out;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 0;
  }

  .delete-button:hover {
    background-color: #dc2626;
  }

  .delete-button:active {
    background-color: #b91c1c;
  }

  .no-meals-message {
    font-size: 1rem;
    color: #6b7280;
    text-align: center;
    width: 100%;
    padding: 1rem 0;
  }
</style>
