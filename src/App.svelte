<script>
  import "./main.css";
  import Summary from "./lib/Summary.svelte";
  import Form from "./lib/Form.svelte";
  import Nutrient from "./lib/Nutrient.svelte";
  let weight = Number(localStorage.getItem("weight")) || 70;
  let height = Number(localStorage.getItem("height")) || 170;
  let gender = Number(localStorage.getItem("gender")) || 1;
  let age = Number(localStorage.getItem("age")) || 20;
  let job = Number(localStorage.getItem("job")) || 1;

  $: {
    // set localStorage
    localStorage.setItem("weight", weight.toFixed(2));
    localStorage.setItem("height", height.toFixed(2));
    localStorage.setItem("gender", gender.toString());
    localStorage.setItem("age", age.toString());
    localStorage.setItem("job", job.toString());
  }

  $: bmrMale = 66 + 13.7 * weight + 5 * height - 6.8 * age;
  $: bmrFemale = 665 + 9.6 * weight + 1.8 * height - 4.7 * age;
  function getTdeeFactorFromJob(job) {
    switch (job) {
      case 1:
        return 1.2;
      case 2:
        return 1.375;
      case 3:
        return 1.55;
      case 4:
        return 1.725;
      case 5:
        return 1.9;
    }
  }

  function getJobText(job) {
    switch (job) {
      case 1:
        return "No Exercise";
      case 2:
        return "Light Exercise (1-2 Days a week)";
      case 3:
        return "Moderate Exercise (3-5 Days a week)";
      case 4:
        return "Heavy Exercise (6-7 Days a week)";
      case 5:
        return "Athlete (twice a day)";
    }
  }
  $: tdeeFactor = getTdeeFactorFromJob(job);
  $: bmr = gender === 1 ? bmrMale : bmrFemale;
  $: tdee = Math.round(bmr * tdeeFactor * 100) / 100;
  $: deficit = tdee - 500;
  $: surplus = tdee + 500;
  $: genderText = gender === 1 ? "Male" : "Female";
  $: jobText = getJobText(job);
</script>

<main class="app">
  <h1>Nutrition Calculator</h1>
  <Form bind:weight bind:height bind:age bind:activityType={job} bind:gender />
  <div class="report">
    <Summary
      bind:age
      bind:bmr
      bind:deficit
      bind:genderText
      bind:jobText
      bind:surplus
      bind:tdee
    />
    <Nutrient bind:weight />
  </div>
</main>

<style>
  .app {
    padding: 16px;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .report {
    display: flex;
    flex-direction: row;
    gap: 16px;
  }
</style>
