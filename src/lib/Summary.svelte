<script>
  export let bmi;
  export let bmr;
  export let tdee;
  export let deficit;
  export let surplus;
</script>

<div class="summary">
  <h2>Summary</h2>
  <p>ดัชนีมวลกาย: {Math.floor(bmi)}</p>
  <p>BMR <span class="info">{bmr?.toFixed(0)}</span>kCal</p>
  <p>TDEE <span class="info">{tdee?.toFixed(0)}</span> kCal</p>
  <h3>ปริมาณพลังงานที่ควรได้รับ</h3>
  <p>ลดไขมัน <span class="info">{deficit?.toFixed(0)}</span> kCal</p>
  <p>
    เพิ่มกล้ามเนื้อ <span class="info">{surplus?.toFixed(0)}</span> kCal
  </p>
</div>

<style>
  .info {
    margin: 4px 8px;
    padding: 4px 8px;
    background-color: hsl(250, 100%, 70%);
    border-radius: 8px;
    color: hsl(250, 100%, 95%);
    font-weight: bold;
  }
  .summary {
    display: flex;
    flex-grow: 1;
    flex-direction: column;
    background-image: linear-gradient(
      to bottom,
      hsl(250, 100%, 90%),
      hsl(300, 100%, 90%)
    );
    padding: 16px;
    border: 1px solid hsl(250, 100%, 75%);
    border-radius: 8px;
    gap: 16px;
  }
  .summary p {
    margin: 0;
  }
</style>
