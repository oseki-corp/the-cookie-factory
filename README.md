# The Cookie Factory for Winterfest 2023

![Baking Octocat](baking-octocat.png)

This repository is a template implementing all actions for the [GitHub Projects](https://github.com/features/issues) [The Cookie Factory](https://github.com/orgs/oseki-corp/projects/11)

If the Project mentioned above is the frontend, this is the backend where all the baking magic happens.

## Components powering the cookie factory

### Recipe fetching workflow

Once a new issue is created or its title updated [this workflow](.github/workflows/food-recipe-issue.yml) is here to fetch:
* The recipe instructions
* The list of ingredients
* A picture of the cookie to bake

The GitHub Project [built-in automation](https://docs.github.com/en/issues/planning-and-tracking-with-projects/automating-your-project/using-the-built-in-automations) is set to add an entry when a new issue or pull request is added to this repository.
Also it is going to set (default) values for fields in the GitHub Project with the help the [titoportas/update-project-fields](https://github.com/marketplace/actions/update-github-project-fields) Actions via GitHub GraphQL API.



🍪🏭
