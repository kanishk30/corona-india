<script>
    import { Button, Card, CardBody } from 'sveltestrap';

export let data = [];
import { afterUpdate} from 'svelte';
// export let data;
const population = 1326093247;
$: recovered = 0;
$: affected = 0;
$: percentRecovered = ((recovered / affected) * 100).toFixed(2);
$: percentAffected = (affected / population) * 100;
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

<Card body color="primary" inverse class="mb-3">
    <CardBody>
      In India, only {affected} people got affected out of which {recovered} already recovered successfully, which is {percentRecovered}% . This makes up only <strong>{percentAffected}% </strong> of the total population as affected.
      <h2>The number speaks for itself, there is NO need to panic. </h2>
    </CardBody>
</Card>