## Testing your policies

### 1. Run the `linter` script

Run the `linter.py` script to catch any syntax errors in your policies.

    python linter.py --gcp <your-service-name>

![linters-output](images/linters-output.PNG)

---

### 2. Run the `OPA eval` commands

Use the following commands to test your policy output.

---

#### `.message`

Displays a basic summary of the policy result.

    opa eval --data .\policies\gcp --data .\policies\_helpers --input .\inputs\gcp\<SERVICE>\<RESOURCE>\<ATTRIBUTE>\plan.json "data.terraform.gcp.security.<SERVICE>.<RESOURCE>.<ATTRIBUTE>.message" --format pretty

![opa-eval-message-output](images/opa-eval-message-output.PNG)

---

#### `.details`

Displays detailed information about the policy evaluation.

    opa eval --data .\policies\gcp --data .\policies\_helpers --input .\inputs\gcp\<SERVICE>\<RESOURCE>\<ATTRIBUTE>\plan.json "data.terraform.gcp.security.<SERVICE>.<RESOURCE>.<ATTRIBUTE>.details" --format pretty

![opa-eval-details-output](images/opa-eval-details-output.PNG)


[contents](policy-writing-totourial.md)


