# Foodpot

## Local Development setup

### Requirements

* node 18
* eas-cli
* npm
* Expo go installed on the phone

### Setup

```
cd foodpot
npm ci
npm run start -- --tunnel
```

Start expo go on the phone, Login to EAS.
scan QR code with Expo go(android) or Camera(IOS)

expo might require login to eas to start. You have to be added to the foodpot EAS project to use same project id. 

to change eas project or remove it, modify this section in `app.json`

```
    "extra": {
      "eas": {
        "projectId": "b5803f48-c974-4e19-8186-c830aef84211"
      }
    },
```

## Simple feature branch workflow

### Development

Start doing feature or fix from clean up-todate main branch. Use feature branches workflow. https://docs.gitlab.com/ee/gitlab-basics/feature_branch_workflow.html

```sh
git checkout main
git fetch
git pull origin main
```

Create new branch
```sh
git checkout -b "feat/name-of-shiny-new-feature"
```
Now do the changes, commit often and merge changes from `main` branch if needed new changes are in main.
When commiting, follow conventional commits standart https://www.conventionalcommits.org/en/v1.0.0/

```
git add <changes>
git commit -m "feat: added search bar"
```

To synchronize with `main`, merge with changes from `main` to your branch:

```
git checkout main
git pull origin main
git chekout "feat/name-of-shiny-new-feature"
git merge main
```

After you are done developing, open pull(merge) request to the main branch from your feature branch

### Definition of Done

* CI checks are successfull
* Make sure feature branch is up-to-date with main.
* Manual QA is done **after** merging with main and CI checks are successfull
* 2 review approvals done by CODEOWNERS
* Pull request is merged with main.
* merged feature branch is deleted
