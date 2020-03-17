<script>
  import {
    Card,
    CardBody,
    ListGroup,
    ListGroupItem
  } from "sveltestrap";
</script>

<div id='cardID'>
  <Card body
    color="success"
    class="mb-3"
    >
    <CardBody>
      <h1>Dos</h1>
      <h6>Practice frequent hand washing.</h6>
      <h6>Cover your nose and
        mouth with
        handkerchief/tissue while
        sneezing and coughing</h6>
      <h6>Throw used
        tissues into closed
        bins immediately
        after use</h6>
      <h6>See a doctor if you feel unwell
        (fever, difficult breathing and
        cough)</h6>
      <h6>Avoid participating
        in large gatherings</h6>
    </CardBody>

  </Card>
  <Card body
    color="danger"
    class="mb-3">
    <CardBody>
      <h1>Donts</h1>
      <h6>Have a close contact
        with anyone, if you’re
        experiencing cough
        and fever</h6>
      <h6>Touch your eyes,
        nose and mouth</h6>
      <h6>nose and mouth Spit in public</h6>
      <h6>Wear face mask if you aren't infected or aren't taking care of individuals infected by Covid19
      </h6>
    </CardBody>

  </Card>
</div>

<style>

  @media screen and (min-width: 481px) {
    #cardID {
      display: flex;
      justify-content: space-around;
    }
  }

  @media only screen and (max-width: 480px) {
    #cardID {
        display: block;
    }
  }

  h6 {
    color: white;
  }

  h1 {
    color: white
  }
</style>