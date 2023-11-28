<getting-started-instructions>
  <h1>Get started for free!</h1>
  <p>
    The free plan comes with all the features and has a lifetime limit of 20,000 credits.
    <a href="/docs/macos/getting-started/">Click here to get started for free</a>.
  </p>
  <h1>Looking for more credits?</h1>
  <p>Check out our subsciption plans below. Get <b>2 months free</b> with a yearly subscription!</p>
</getting-started-instructions>
<existing-user-instructions>
  <h1>Purchase a subscription</h1>
  <p class="instruction-text">Get <b>2 months free</b> with a yearly subscription!</p>
</existing-user-instructions>

<script async src="https://js.stripe.com/v3/pricing-table.js"></script>
<div style="margin: 30px 0">
  <stripe-pricing-table
    pricing-table-id="prctbl_1NjsheD2JBiQZxokSpWULstH"
    publishable-key="pk_live_51NJTTND2JBiQZxokSKTb96ZTSoFpzpGwdj9thFtEmVI3NxBficMiv94UL8ZsbzWoXDr2RSIyDPUk29x52ENrlvmR00bR04qY5j">
  </stripe-pricing-table>
</div>

<p>
  * Each AI model consumes different amounts of credits
</p>
<table>
  <tr>
    <th>Model</th>
    <th>1 token consumes</th>
  </tr>
  <tr>
    <td>gpt-3.5-turbo</td>
    <td>1 credit</td>
  </tr>
  <tr>
    <td>gpt-4</td>
    <td>30 credit</td>
  </tr>
  <tr>
    <td>gpt-4-1106-preview</td>
    <td>15 credit</td>
  </tr>
</table>
<p>
  Here are some helpful rules of thumb for understanding tokens:
</p>
<ul>
  <li>1 token ~= 4 characters in English</li>
  <li>1 token ~= ¾ words</li>
  <li>100 tokens ~= 75 words</li>
</ul>
<script>
  const urlParams = new URLSearchParams(window.location.search);
  const customerEmail = urlParams.get("customer-email");
  if (customerEmail) {
    document.querySelector("getting-started-instructions").remove();
    const stripePricingTable = document.querySelector(
      "stripe-pricing-table"
    );
    stripePricingTable.setAttribute("customer-email", customerEmail);
  } else {
    document.querySelector("existing-user-instructions").remove();
  }
</script>