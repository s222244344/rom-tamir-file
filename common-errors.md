## Errors you may face

If you haven’t included all the required attributes when writing your policies, Terraform will fail when trying to execute your plan. You may receive an error like this:

![Failed-terraform-plan](images/failed-terraform-plan.PNG)

---

The output explains that the required field `project` is not set in the `c.tf` and `nc.tf` files.

It may also indicate that other required fields, such as `region`, are missing.

---

### How to fix

Ensure that all required attributes are included in both your `c.tf` and `nc.tf` files. For example:

```rego
resource "google_cloudfunctions_function" "c" {
  name                = "c"
  runtime             = "node.js20"
  region              = "google_cloudfunctions_function.function.region"
  project             = "google_cloudfunctions_function.function.project"
  available_memory_mb = 128
}
```
and 

```rego
resource "google_cloudfunctions_function" "nc" {
  name                = "nc"
  runtime             = "node.js10"
  region              = "google_cloudfunctions_function.function.region"
  project             = "google_cloudfunctions_function.function.project"
  available_memory_mb = 4444
}
```

[contents](policy-writing-totourial.md)
