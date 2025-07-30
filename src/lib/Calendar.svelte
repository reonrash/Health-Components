<script>
  let currentMonth = new Date().getMonth();
  let currentYear = new Date().getFullYear();

  const mockDayPercentages = {
    1: 75,
    2: 0,
    3: 88,
    4: 15,
    5: 90,
    6: 55,
    7: 40,
    8: 65,
    9: 25,
    10: 45,
    11: 70,
    12: 33,
    13: 95,
    14: 10,
    15: 60,
    16: 48,
    17: 82,
    18: 22,
    19: 77,
    20: 100,
    21: 85,
    22: 38,
    23: 92,
    24: 5,
    25: 68,
    26: 42,
    27: 80,
    28: 28,
    29: 72,
    30: 50,
    31: 51,
  };

  const generateDays = (month, year) => {
    const date = new Date(year, month, 1);
    const firstDayIndex = date.getDay();
    const numDays = new Date(year, month + 1, 0).getDate();

    let days = [];

    for (let i = 0; i < firstDayIndex; i++) {
      days.push(null);
    }

    for (let i = 1; i <= numDays; i++) {
      days.push(i);
    }
    return days;
  };

  $: daysInMonth = generateDays(currentMonth, currentYear);

  const getMonthName = (monthIndex) => {
    const date = new Date(currentYear, monthIndex);
    return date.toLocaleString("default", { month: "long" });
  };
</script>

<div class="calendar-container">
  <div class="calendar-card">
    <div class="calendar-header">
      <h2 class="calendar-title">
        {getMonthName(currentMonth)}
        {currentYear}
      </h2>
    </div>

    <div class="days-of-week">
      {#each ["S", "M", "T", "W", "T", "F", "S"] as day}
        <div class="day-of-week-item">{day}</div>
      {/each}
    </div>

    <div class="calendar-grid">
      {#each daysInMonth as day, index}
        <div class="day-cell">
          {#if day !== null}
            {@const percentage = mockDayPercentages[day]}
            <div
              class="day-number-square"
              style="
                width: {percentage > 0 ? `${percentage * 0.04}rem` : '0rem'};
                height: {percentage > 0 ? `${percentage * 0.04}rem` : '0rem'};
                background-color: {percentage > 0 ? '#4ade80' : 'transparent'};
                color: #1f2937;
              "
            >
              {day}
            </div>
          {:else}
            <div></div>
          {/if}
        </div>
      {/each}
    </div>
  </div>
</div>

<style>
  * {
    margin: 0;
    font-family: Arial, sans-serif;
  }

  .calendar-container {
    min-height: 400px;
    background-color: #f3f4f6;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
  }

  @media (min-width: 640px) {
    .calendar-container {
      padding: 1.5rem;
    }
  }

  @media (min-width: 1024px) {
    .calendar-container {
      padding: 2rem;
    }
  }

  .calendar-card {
    background-color: #ffffff;
    border-radius: 0;
    box-shadow:
      0 20px 25px -5px rgba(0, 0, 0, 0.1),
      0 10px 10px -5px rgba(0, 0, 0, 0.04);
    padding: 1.5rem;
    width: 100%;
    max-width: 28rem;
  }

  .calendar-header {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin-bottom: 1.5rem;
  }

  .calendar-title {
    font-size: 2.25rem;
    font-weight: 700;
    color: #1f2937;
    line-height: 1;
  }

  .days-of-week {
    display: grid;
    grid-template-columns: repeat(7, minmax(0, 1fr));
    text-align: center;
    font-size: 0.95rem;
    font-weight: 700;
    color: #4b5563;
    margin-bottom: 1rem;
  }

  .day-of-week-item {
    padding-top: 0.5rem;
    padding-bottom: 0.5rem;
  }

  .calendar-grid {
    display: grid;
    grid-template-columns: repeat(7, minmax(0, 1fr));
    gap: 0.25rem;
    text-align: center;
  }

  .day-cell {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 4rem;
    width: 100%;
    border-radius: 0;
    overflow: hidden;
    transition: all 0.2s ease-in-out;
  }

  .day-number-square {
    position: relative;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 0;
    font-size: 1.25rem;
    font-weight: 600;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease-in-out;
  }
</style>
