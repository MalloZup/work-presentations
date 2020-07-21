# Github-actions Overview and concrete RFC for test Pull-requests


Dario Maiocchi @SUSE

---

# GitHub actions can do lot of things.

- Release automation (issues, or Releases workflow) using DSL instead of api scripts

- Pull-Request tests

- ...


---

# Github base on ideas of:

* Jenkins
* Travis
* Circleci


* Jenkins
Worker/master model, multiple worker/agents internally, and target them via labels

* Travis Circle/CI:
Easy DSL sytanx in yaml, run natively in github 

* It avoid also the creation/maintenance of custom scripts using API. 

---

# Case-Study: Sap-Ha deployment testing prs:


# Components:

* Github-action worker:
 https://gitlab.suse.de/shap/shap-ops/-/tree/master/github-action-agent


* The pipeline/workflow:
https://github.com/MalloZup/ha-sap-terraform-deployments/blob/fake/.github/workflows/terraform-only-e2e.yaml#L1


* Comprehensible Data driven workflow
Instead of maintaining script with embedded logic, we just pass the terraform file with data.
https://gitlab.suse.de/shap/shap-ops/-/blob/master/github-action-agent/hana-netweaver-tf-only.tfvars

---
## Example:

https://github.com/MalloZup/ha-sap-terraform-deployments/runs/630345949

---

# Nexts step:

* create terraform validation on pr
* create salt validation + terraform on pr

---

# Other ideas.
automate releases with github actions instead of scripts

---
## Unresolved/undone things:

Currenlty the terraform.tf file is on gitlab.

Usee Github with Secrets for sensitive data, so a PR which  modify the vars we can adapt them.

It will also make create an automated tested documentation/template.

