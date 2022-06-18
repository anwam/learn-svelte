<script>
  export let weight;
  export let height;
  export let age;
  export let gender;
  export let activityType;

  $: bmi = Math.round((weight / Math.pow(height / 100, 2)) * 100) / 100;
</script>

<div class="calculator">
  <div class="input">
    <label for="age">อายุ</label>
    <input type="number" id="age" placeholder="age (year)" bind:value={age} />
  </div>

  <div class="input">
    <p>เพศ</p>
    <input type="radio" id="male" bind:group={gender} value={1} />
    <label for="male">ผู้ชาย</label>
    <input type="radio" id="female" bind:group={gender} value={2} />
    <label for="female">ผู้หญิง</label>
  </div>

  <div class="input">
    <p>กิจกรรม</p>
    <select bind:value={activityType} name="activity" id="activity">
      <option value={1}>ไม่ออกกำลังกาย</option>
      <option value={2}>ออกกำลังกายเบาๆ (1-2 ครั้งต่อสัปดาห์)</option>
      <option value={3}>ออกกำลังกายหนักปานกลาง (3-5 ครั้งต่อสัปดาห์)</option>
      <option value={4}>ออกกำลังกายหนัก (6-7 ครั้งต่อสัปดาห์)</option>
      <option value={5}>นักกีฬา (ออกวันละ 2 ครั้ง)</option>
    </select>
  </div>

  <div class="input">
    <label for="weight">น้ำหนัก</label>
    <input
      type="number"
      id="weight"
      placeholder="weight (kg)"
      bind:value={weight}
    />
    <label for="height">ส่วนสูง</label>
    <input
      type="number"
      id="height"
      placeholder="height (cm)"
      bind:value={height}
    />
  </div>

  <p>ดัชนีมวลกาย: {bmi.toFixed(2)}</p>
</div>

<style>
  .calculator {
    display: flex;
    flex-direction: column;
    background-color: hsl(203, 100%, 95%);
    padding: 16px;
    border: 1px solid hsl(203, 100%, 75%);
    border-radius: 8px;
    gap: 16px;
  }

  .input {
    display: flex;
    flex-direction: row;
    gap: 16px;
    align-items: center;
  }

  label {
    font-weight: bold;
  }

  p {
    margin: 0;
    font-weight: bold;
  }

  input,
  select {
    padding: 8px;
    border: 1px solid hsl(203, 100%, 75%);
    border-radius: 8px;
  }
</style>
