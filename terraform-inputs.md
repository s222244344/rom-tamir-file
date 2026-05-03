## Terraform inputs

Make sure you are in the inputs directory of the attribute you are writing your policy on:

`inputs/gcp/service_name/resource/argument reference(policy)`

---

### 1. terraform init

    terraform init

![Terraform-init](images/terraform-init.png)

---

### 2. get binary plan

    terraform plan --out=plan

![get-binary-plan](images/terraform-plan--out.PNG)

---

### 3. turn plan into .json file

    terraform show -json plan > plan.json

![turn-plan-into-.json](images/plan-json.PNG)


[contents](policy-writing-totourial.md)


