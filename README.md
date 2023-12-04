# The Cookie Factory for Winterfest 2023

![Baking Octocat](baking-octocat.png)

This repository is a template implementing all actions for the [GitHub Projects](https://github.com/features/issues) [The Cookie Factory](https://github.com/orgs/oseki-corp/projects/11)

If the Project mentioned above is the frontend, this is the backend where all the baking magic happens.

## Components powering the cookie factory

### 1. Recipe fetching workflow

Once a new issue is created or its title updated [this workflow](.github/workflows/food-recipe-issue.yml) is here to fetch:
1. The recipe instructions
2. The list of ingredients
3. A picture of the cookie to bake

The GitHub Project [built-in automation](https://docs.github.com/en/issues/planning-and-tracking-with-projects/automating-your-project/using-the-built-in-automations) is set to add an entry when a new issue or pull request is added to this repository.
Also it is going to set (default) values for fields in the GitHub Project with the help the [titoportas/update-project-fields](https://github.com/marketplace/actions/update-github-project-fields) Actions via GitHub GraphQL API.

The workflow needs the following [Actions secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#about-secrets) to operate properly:
* `FOOD_RECIPES_KEY` which contains the API towards the [Food recipes with images](https://rapidapi.com/zilinskivan/api/food-recipes-with-images) endpoint key.
* `PROJECT_KEY` which contains a [GitHub Personal Access Token (classic)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#personal-access-tokens-classic) granting `project`, `read:org` and `repo` access to automatically modify issues and projects within the repo

Additionaly these [Actions variables](https://docs.github.com/en/actions/learn-github-actions/variables#about-variables) are needed:

* `PROJECT_ID` is the GraphQL project id which can be viewed with the GH CLI command `gh project list`. This ID looks like `PVT_XXXXXXXXXXXXXXXX`
* `PROJECT_URL` is the project URL to update (e.g `https://github.com/orgs/<org-name>/projects/<project-number>` or `https://github.com/users/<username/projects/<project-number>`)

### 2. Cookie baking workflow

Once an issue of this repo gets the issue label `Baking`, it will start the baking process which will be reflected live in the `Progress` field updated by the [titoportas/update-project-fields](https://github.com/marketplace/actions/update-github-project-fields) Actions.
In the end, the issue will be automatically closed by the Actions [peter-evans/close-issue](https://github.com/marketplace/actions/close-issue) which will change the issue status to `Done`.

The workflow needs the following [Actions secrets](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#about-secrets) to operate properly:
* `FOOD_RECIPES_KEY` which contains the API towards the [Food recipes with images](https://rapidapi.com/zilinskivan/api/food-recipes-with-images) endpoint key.
* `PROJECT_KEY` which contains a [GitHub Personal Access Token (classic)](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#personal-access-tokens-classic) granting `project`, `read:org` and `repo` access to automatically modify issues and projects within the repo

Additionaly these [Actions variables](https://docs.github.com/en/actions/learn-github-actions/variables#about-variables) are needed:

* `PROJECT_ID` is the GraphQL project id which can be viewed with the GH CLI command `gh project list`. This ID looks like `PVT_XXXXXXXXXXXXXXXX`
* `PROJECT_URL` is the project URL to update (e.g `https://github.com/orgs/<org-name>/projects/<project-number>` or `https://github.com/users/<username/projects/<project-number>`)

Happy baking! 🍪 🏭
