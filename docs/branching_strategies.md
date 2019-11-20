# branching strategies

---

## Branch to env mapping
* [Env branch mapping](https://www.wearefine.com/mingle/env-branching-with-git/)
* [gitlab flow](https://docs.gitlab.com/ee/workflow/gitlab_flow.html)
* [oneflow](http://endoflineblog.com/oneflow-a-git-branching-model-and-workflow) (gitflow with one instead of two long-living branches)

### branch -> env
* prod -> prod
* mo -> mo
* qa -> qa
* **master** -> dev (feature branches are created from master)
    * specific tagged commits can be deployed from master to any of the dev or qa envs

  Env configs can be generated with a combination of env vars and other source-controlled files


