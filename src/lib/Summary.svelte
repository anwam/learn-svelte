<script>
  export let genderText;
  export let jobText;
  export let age;
  export let bmr;
  export let tdee;
  export let deficit;
  export let surplus;
</script>

<div class="summary">
  <h2>Summary</h2>
  <p>Gender: {genderText}</p>
  <p>Activity Type: {jobText}</p>
  <p>Age: {age}</p>
  <p>BMR: {bmr.toFixed(2)}</p>
  <p>TDEE: {tdee.toFixed(2)}</p>
  <p>To get lean {deficit.toFixed(2)} kCal</p>
  <p>
    To get bulk {surplus.toFixed(2)} kCal
  </p>
</div>

<style>
  .summary {
    display: flex;
    flex-grow: 1;
    flex-direction: column;
    background-color: hsl(265, 100%, 95%);
    padding: 16px;
    border: 1px solid hsl(265, 100%, 75%);
    border-radius: 8px;
    gap: 16px;
  }
  .summary p {
    margin: 0;
  }
</style>
