---
layout: default
---

<div class="container">
  <getting-started-instructions>
    <div class="row align-items-center py-4">
      <div class="text-center">
        <h1 class="display-6 fw-bold mb-3">
          Get started <span style="color: #56877c;">for free</span>
        </h1>
      </div>
      <div class="col-md-8 offset-md-2 col-lg-6 offset-lg-3 text-center">
        <p class="fs-5 mb-5">
          The free plan includes all paid features and has a lifetime limit of 20,000 <a href="#what-is-a-credit">credits</a> and 75 <a href="https://chat.openai.com/g/g-611zFFIQR-chatpc-connect-with-macos" target="_blank">ChatPC GPT</a> actions.
        </p>
        <div class="d-grid gap-2 d-md-flex justify-content-md-center mb-5">
          <a class="btn btn-primary px-4 me-md-2" href="/docs/macos/getting-started/">Get started for free</a>
        </div>
      </div>
      <div class="text-center">
        <h1 class="display-6 fw-bold mb-3">
          Looking for more credits?
        </h1>
      </div>
      <div class="col-md-8 offset-md-2 col-lg-6 offset-lg-3 text-center">
        <p class="fs-5">
          Check out our subsciption plans below.<br/>Get <b>2 months free</b> with a yearly subscription!
        </p>
      </div>
    </div>
  </getting-started-instructions>

  <existing-user-instructions>
    <div class="row align-items-center py-4">
      <div class="text-center">
        <h1 class="display-6 fw-bold mb-3">
          Purchase a subscription
        </h1>
      </div>
      <div class="col-md-8 offset-md-2 col-lg-6 offset-lg-3 text-center">
        <p class="fs-5">
          Get <b>2 months free</b> with a yearly subscription!
        </p>
      </div>
    </div>
  </existing-user-instructions>

  <script async src="https://js.stripe.com/v3/pricing-table.js"></script>
  <div style="margin-bottom: 30px">
    <stripe-pricing-table
      pricing-table-id="prctbl_1NjsheD2JBiQZxokSpWULstH"
      publishable-key="pk_live_51NJTTND2JBiQZxokSKTb96ZTSoFpzpGwdj9thFtEmVI3NxBficMiv94UL8ZsbzWoXDr2RSIyDPUk29x52ENrlvmR00bR04qY5j">
    </stripe-pricing-table>
  </div>

  <p id="what-is-a-credit">
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
</div>