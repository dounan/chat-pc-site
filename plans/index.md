<getting-started-instructions>
  <h1>Get started for free!</h1>
  <p class="instruction-text">
    Follow the <a href="/docs/macos/getting-started/">MacOS getting started guide</a>.
  </p>
  <p>Currently only compatible with MacOS 13.0 and above.</p>
  <p>Get <b>2 months free</b> with a yearly subscription!</p>
</getting-started-instructions>
<existing-user-instructions>
  <h1>Purchase a subscription</h1>
  <p class="instruction-text">Choose the plan that works for you.</p>
</existing-user-instructions>
<script async src="https://js.stripe.com/v3/pricing-table.js"></script>
<stripe-pricing-table
  pricing-table-id="prctbl_1NjsheD2JBiQZxokSpWULstH"
  publishable-key="pk_live_51NJTTND2JBiQZxokSKTb96ZTSoFpzpGwdj9thFtEmVI3NxBficMiv94UL8ZsbzWoXDr2RSIyDPUk29x52ENrlvmR00bR04qY5j">
</stripe-pricing-table>
<p>
  * Each AI model consumes different amounts of credits
</p>
<ul>
  <li>GPT-3: 1 token consumes 1 credit</li>
  <li>GPT-4: 1 token consumes 20 credits</li>
</ul>
<p>
  Here are some helpful rules of thumb for understanding tokens in terms of lengths:
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