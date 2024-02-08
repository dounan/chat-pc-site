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
          The free plan includes all paid features and has a lifetime limit of 20,000 <a href="#what-is-a-credit">credits</a> and 75 ChatPC GPT <a href="#what-is-an-action">actions</a>.
        </p>
        <div class="d-grid gap-2 d-md-flex justify-content-md-center mb-5">
          <a class="btn btn-primary px-4 me-md-2" href="/docs/macos/getting-started/">Get started for free</a>
        </div>
      </div>
      <div class="text-center">
        <h1 class="display-6 fw-bold mb-3">
          Want more credits?
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
  <div style="margin-bottom: 50px">
    <stripe-pricing-table
      pricing-table-id="prctbl_1NjsheD2JBiQZxokSpWULstH"
      publishable-key="pk_live_51NJTTND2JBiQZxokSKTb96ZTSoFpzpGwdj9thFtEmVI3NxBficMiv94UL8ZsbzWoXDr2RSIyDPUk29x52ENrlvmR00bR04qY5j">
    </stripe-pricing-table>
  </div>

  <div class="row align-items-center py-4">
    <div class="col-xl-10 offset-xl-1 border rounded-3 p-4">
      <h1 class="h4 mb-3" id="what-is-a-credit">
        What is a credit?
      </h1>
      <p>
        Credits are consumed whenever you communicate with the ChatPC AI. Every word that is given to the AI — both from your prompts and from the results of an action, such as the contents of a file — and every word that the AI generates as output consumes credits.
      </p>
      </p>
        The number of credit consumed depends on the number of characters in a word and the AI model used. The following table shows  <b>approximately</b> how many words you get for each AI model.
      </p>
      <table class="table table-striped">
        <thead>
          <tr>
            <th scope="col">Model</th>
            <th scope="col">1,000 credits</th>
            <th scope="col">Basic</th>
            <th scope="col">Standard</th>
            <th scope="col">Pro</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">gpt-3.5-turbo</th>
            <td>~750 words</td>
            <td>~750,000 words</td>
            <td>~1,875,000 words</td>
            <td>~3,000,000 words</td>
          </tr>
          <tr>
            <th scope="row">gpt-4</th>
            <td>~30 words</td>
            <td>~30,000 words</td>
            <td>~75,000 words</td>
            <td>~120,000 words</td>
          </tr>
          <tr>
            <th scope="row">gpt-4-1106-preview</th>
            <td>~60 words</td>
            <td>~60,000 words</td>
            <td>~150,000 words</td>
            <td>~240,000 words</td>
          </tr>
        </tbody>
      </table>
      <h1 class="h4 mt-5 mb-3" id="what-is-an-action">
        What is a ChatPC GPT action?
      </h1>
      <p>
        A <a href="https://chat.openai.com/g/g-611zFFIQR-chatpc-connect-with-macos" target="_blank">ChatPC GPT</a> action is counted whenever the GPT interact with your macOS (e.g. create a file, compose an email). Credits are not consumed when using the ChatPC GPT.
      </p>
    </div>
  </div>

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