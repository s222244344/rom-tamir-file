## What goes into your `c.tf` and `nc.tf`

### c.tf

Your `c.tf` (compliant.tf) contains the **remedies** in your policy that make it compliant/passable.  
It must include all the required arguments and define the policy using compliant examples.

---

### Example

Service: `cloud_functions`  
Resource type: `google_cloudfunctions_function`
---

### Example c.tf

```rego                                                                     
resource "google_cloudfunctions_function" "c" {
  name              = "example-function"
  runtime           = "nodejs20"
  available_memory_mb = 256
  region            = "us-central1"
  project           = "your-project-id"
}
```
## Writing the c.tf File

### 1. Replace `"RESOURCE TYPE"` with your resource from Terraform

```rego
resource "RESOURCE_TYPE" "c" {

}
```

### 2. Input compliant values for the required arguments

Use the Terraform documentation to identify all **required arguments** and provide valid (compliant) values.

![required-arguments](images/required-arguments.PNG)

Example:

```rego
resource "google_cloudfunctions_function" "c" {
  name                = "c"
  runtime             = "nodejs20"
  region              = "google_cloudfunctions_function.function.region"
  project             = "google_cloudfunctions_function.function.project"
}
```

### 3. Input compliant values for the argument you are writing your policy on

From your research on your service’s arguments, you should know what to input so the policy is compliant.

### Example: `available_memory_mb`


![optional-arguments](images/optional-argument.PNG)

```rego
resource "google_cloudfunctions_function" "c" {
  name                = "c"
  runtime             = "nodejs20"
  region              = "google_cloudfunctions_function.function.region"
  project             = "google_cloudfunctions_function.function.project"
  available_memory_mb = 256
}
```

### nc.tf

Your `nc.tf` (not compliant.tf) contains the remedies in your policy that are **not** compliant/passable. It must include all the required arguments and the policy you are writing with non-compliant examples.

### 1. Replace `"RESOURCE TYPE"` with your resource from Terraform

```rego
resource "RESOURCE_TYPE" "nc" {

}
```
### 2. Input non compliant values for the required arguments

Use the Terraform documentation to identify all **required arguments** and provide invalid (non-compliant) values.

![required-arguments](images/required-arguments.PNG)

Example:

```rego
resource "google_cloudfunctions_function" "nc" {
  name                = "nc"
  runtime             = "nodejs.10"
  region              = "google_cloudfunctions_function.function.region"
  project             = "google_cloudfunctions_function.function.project"
}
```

### 3. Input non compliant values for the argument you are writing your policy on

From your research on your service’s arguments, you should know what to input so the policy is not compliant.

### Example: `available_memory_mb`

![optional-arguments](images/optional-argument.PNG)

```rego
resource "google_cloudfunctions_function" "nc" {
  name                = "nc"
  runtime             = "node.js10"
  region              = "google_cloudfunctions_function.function.region"
  project             = "google_cloudfunctions_function.function.project"
  available_memory_mb = 4444
}
```

When completed move onto to  [Terraform inputs](terraform-inputs.md) 
or back to [Policy Writing](policy-writing.md) 

[contents](policy-writing-totourial.md)
