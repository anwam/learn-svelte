<script>
  export let tdee;
  let proteinRatio = 35;
  let carbRatio = 40;
  let fatRatio = 25;
  $: proteinCalories =
    Math.round(Math.ceil((tdee * proteinRatio) / 100) / 10) * 10;
  $: protein = proteinCalories / 4;
  $: carbCalories = Math.round(Math.ceil((tdee * carbRatio) / 100) / 10) * 10;
  $: carb = carbCalories / 4;
  $: fatCalories = Math.round(Math.ceil((tdee * fatRatio) / 100) / 10) * 10;
  $: fat = fatCalories / 9;
</script>

<div class="nutrient">
  <h2>Nutrients</h2>
  <p>
    อัตราส่วน
    <span>P{proteinRatio}:C{carbRatio}:F{fatRatio}</span>
  </p>
  <p>
    โปรตีน <span class="info">{protein?.toFixed(2)} g</span>ได้ {proteinCalories}
    kCal
  </p>
  <p>
    Carb <span class="info">{carb?.toFixed(2)}g</span> ได้ {carbCalories} kCal
  </p>
  <p>
    ไขมัน <span class="info">{fat?.toFixed(2)}g</span>ได้ {fatCalories} kCal
  </p>
</div>

<style>
  .info {
    margin: 4px 8px;
    padding: 4px 8px;
    background-color: hsl(300, 100%, 80%);
    border-radius: 8px;
    color: hsl(300, 100%, 30%);
    font-weight: bold;
  }
  p {
    margin: 0;
  }
  .nutrient {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    background-image: linear-gradient(
      to bottom,
      hsl(300, 100%, 90%),
      hsl(351, 100%, 90%)
    );
    padding: 16px;
    border: 1px solid hsl(300, 100%, 75%);
    border-radius: 8px;
    gap: 16px;
  }
</style>
