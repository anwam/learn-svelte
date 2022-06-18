<script>
  export let weight;
  let protein = weight * 2;
</script>

<div class="nutrient">
  <h2>Nutrients</h2>
  <p>Weight {weight}</p>
  <p>Daily Protein Intake: {protein} grams</p>
</div>

<style>
  p {
    margin: 0;
  }
  .nutrient {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    background-color: hsl(30, 100%, 95%);
    padding: 16px;
    border: 1px solid hsl(30, 100%, 75%);
    border-radius: 8px;
    gap: 16px;
  }
</style>
