<script>
</script>

<h2>Know the Symptoms and ACT</h2>
<div class="sections">
  <div class="card">
    <img src='images/fever.png'>
    <p>High Fever</p>
  </div>
  <div class="card">
    <img src="images/breath.png">
    <p>Shortness of breadth</p>
  </div>
  <div class="card">
    <img src='images/cough.png'>
    <p>Dry cough</p>
  </div>
</div>

<style>
  .sections {
    margin: 32px 0;
    color: #E2E8F0;
    justify-content: space-around;
    display: flex;
    flex-wrap: wrap;
  }
  @media only screen and (max-width: 480px) {
    .sections {
        display: block;
    }
  }
  h2 {
    margin: 24px 0;
    display: flex;
    justify-content: space-evenly;
  }
  .card {
    flex-basis: 25%;
    background-color: #ff188c;
    border-radius: 0.5rem;
    height: 100%;
    padding: 3rem 1.5rem;
    box-shadow: 0 0px 1px 0 rgba(0,0,0,0.4), 0 1px 2px 0 rgba(0,0,0,0.06);
  }
  img {
    margin-left: auto;
    margin-right: auto;
    padding-bottom: 1.5rem;
    width: 8rem;
    height: 8rem;
  }
  p {
    text-align: center;
    font-weight: 700;
    font-size: 20px;
    line-height: 0;
    color: #fff
  }
</style>