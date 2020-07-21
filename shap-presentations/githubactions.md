# Github action part 02

---
 tests prs without having to maintian an inhouse script wich communicate via api from jenkins or scheduler to github.
( other teams do SUSE-manager, Caasp, or SCC use this).

Another possible use-case would be to test release branches.

Relases branch != github prs


---

### Self-hosted worker, what was the problem:

- selfhosted worker works but it can't use secrets variables. (this can be used only for a release branch test)

- For our and lot of other use-cases this is a major missing feature . ( we can't pass credentials etc)
---

### Using Vault  for storing secrets and pass them to worker

Vault is secret key value server


I have create more doc at https://github.com/MalloZup/vault-opensuse

### Pro/Cons:

- pro:
We can manage credentials and secrets and pass them like 

```export TF_VAR_qemu_uri=`vault kv get -field=qemu_uri secret/github```

- cons:

A part beeing a service to maintain with it is own semantic, it is not 100% sure in this context because we need alwasy to authenticate and pass the token on the workflow.


---


# Last minute major issue: 

Worker try to automatic updates (without user control) and cause container to crash :/
https://github.com/actions/runner/issues/484


# Resumes:

the last major issue is kind frustating and impact the way we use the container, so that we can't use the worker inside the container until the issue is fixed.


