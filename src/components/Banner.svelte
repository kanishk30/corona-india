<script>
    import { Button, Card, CardBody } from 'sveltestrap';

export let data = [];
import { afterUpdate} from 'svelte';
// export let data;
const population = 1326093247;
$: recovered = 0;
$: affected = 0;
$: percentRecovered = ((recovered / affected) * 100).toFixed(2);
$: percentAffected = ((affected / population) * 100).toFixed(6);
afterUpdate(() => {
  console.log(data, 'dataBanner');
  getAffectedPopulation(data);
})

function getAffectedPopulation(data) {
  let india = data.filter((obj) => obj.country === 'India')[0];
  affected = india.cases;
  recovered = india.recovered
}

</script>

<!-- <Card body color="primary" inverse class="mb-3">
    <CardBody>
      In India, only {affected} people got affected out of which {recovered} already recovered successfully, which is {percentRecovered}% . This makes up only <strong>{percentAffected}% </strong> of the total population as affected.
      <h2>The number speaks for itself, there is NO need to panic. </h2>
    </CardBody>
</Card> -->

<section>
  <p class="text">
      In India, {affected} people got affected from Covid19 which makes up <strong>{percentAffected}% </strong> of the total population. {recovered} already recovered successfully, which is {percentRecovered}%.
      The number speaks for itself, there is NO need to panic.
  </p>
</section>

<style>
  section {
    background: #2bbdd4;
    padding: 24px;
    width: 50%;
  }
  .heading {
    color: white;

    font-size: larger;
    margin: 1rem 0;

  }

  .text {
    color: white;
    font-size: 24px;
    line-height: 2;
  }

</style>