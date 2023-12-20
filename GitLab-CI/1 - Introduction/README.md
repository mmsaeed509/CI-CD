Create a Pipeline:

- create a `.gitlab-ci.yml` YAML file.
- create your jobs in the YAML file.
- save and commit 
- GitLab will detect the file and run your Pipeline

Notes:

- after the job is finished all data are deleted
- so, you can use `artifacts` to save all data

```yaml
  artifacts:
    paths:
      - build/
```
