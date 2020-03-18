<script>
  import {
    Card,
    CardBody,
    ListGroup,
    ListGroupItem
  } from "sveltestrap";
</script>

<div id='cardID'>
    <div class="left">
      <h3>DOs</h3>
      <p>Stay home when you are sick.</p>
<p>Avoid touching your eyes, nose, and mouth.</p>
<p>Clean AND disinfect frequently touched surfaces daily.</p>
<p>Cover your cough or sneeze with a tissue, then throw the tissue in the trash.</p>
<p>Avoid close contact with people who are sick.</p>
<p>Wash your hands often with soap and water for at least 20 seconds, especially after going to the bathroom; before eating; and after blowing your nose, coughing, or sneezing. </p>
    </div>

    <div class="right">
      <h3>DONTs</h3>
      <p>Shake hands with others</p>
<p>Touch your eyes, nose or mouth if your hands are not clean</p>
<p>Wear face mask if you aren't infected or aren't taking care of individuals infected by Covid19</p>
<p>Go to to pharmacy or hospital. If you have corona like symptoms, call 1500 instead</p>
<p>Go out in groups or where there are a large number of people. Avoid crowds as much as possible</p>
    </div>
</div>

<style>

  @media screen and (min-width: 481px) {
    #cardID {
      display: flex;
      justify-content: space-between;
      margin: 48px 0;
        /* background-color: black; */

    }
  }

  @media only screen and (max-width: 480px) {
    #cardID {
        display: block;
        /* background-color: black; */
    }
  }

  .left {
    flex-basis: 45%;
    background-color: rgb(19, 153, 108);
    padding: 24px;
  }
  .right {
    text-align: right;
    flex-basis: 45%;
    background-color: rgb(194, 16, 16);
    padding: 24px;
  }

  p {
    color: white;
    line-height: 30px;
    font-size: 20px;
  }

  h3 {
    color: white
  }
</style>