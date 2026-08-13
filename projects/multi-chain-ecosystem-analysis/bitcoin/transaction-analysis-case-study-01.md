

### One important improvement

Notice what this does differently from a generic blockchain project.

We're explicitly separating:

**FACT**
> The transaction has X inputs and Y outputs.

**INFERENCE**
> Output #1 may represent change.

**ATTRIBUTION**
> This address belongs to a particular person/entity.

That distinction is **excellent analyst practice**, particularly for the kind of blockchain intelligence, AML, compliance, and investigative roles we're targeting.

Mempool's public API specifically supports the fields we're using here—transaction details, inputs/outputs, status, block information, address history, UTXOs, and output-spending status. :contentReference[oaicite:1]{index=1}

### One thing I need you to do

**Don't fill in the TXID yourself yet.**

Once you've created the file, tell me **"created"**.

Then we'll select a suitable **public Bitcoin transaction together**, retrieve its actual data, and complete the case study with real numbers.

That will give you your **first genuine hands-on blockchain-analysis artifact** in GitHub.
