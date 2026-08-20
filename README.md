# My Agenda

My Agenda is a public, static four-quadrant agenda app. The shared agenda lives in [`agenda.json`](./agenda.json), so every device can load the same data from this repository.

It organises tasks into:

- Urgent and important
- Urgent but not important
- Important but not urgent
- Not important and not urgent

## Features

- Add, edit, delete, and complete tasks.
- Move a task to another quadrant while editing.
- Generate a copyable prompt for ChatGPT to polish the complete agenda in concise British English.
- Load the public `agenda.json` automatically when the app opens.
- Save the current agenda to GitHub with one click, creating a public commit.
- Keep a local browser copy for fast editing and offline fallback.
- Export and import the agenda as JSON.

## Public-data model

This repository is public. Anyone can read the agenda, its task text, and its complete commit history. Anyone may also copy or fork the repository.

Only the repository owner or a GitHub collaborator with write permission can save directly to this repository. The app checks the token's repository write permission before it creates a commit. Other people can read the agenda but cannot edit `agenda.json` in this repository.

Every successful save is a normal GitHub commit, so do not put private or sensitive information in the agenda.

## One-time GitHub sync setup

Because this is a static GitHub Pages site, it uses a fine-grained personal access token instead of a browser-based GitHub login. The app never receives your GitHub password. The token is masked and kept only in the current browser tab.

1. Open GitHub's [new fine-grained token page](https://github.com/settings/personal-access-tokens/new).
2. Give the token a name such as **My Agenda Save** and choose an expiry date.
3. Under **Repository access**, choose **Only select repositories**, then select **My-Agenda**.
4. Under **Repository permissions**, set **Contents** to **Read and write**. Leave other permissions at their defaults.
5. Generate the token and copy it immediately. GitHub will not show the complete token again.
6. Open the agenda site, expand **One-time GitHub sync setup**, paste the token, and select **Connect token**.
7. Select **Save to GitHub** to create a public commit in `agenda.json`.

Use a separate token on each device or browser tab. The token expires according to the expiry date chosen on GitHub. The previous GitHub App and Device Flow setup is not required.

For more information, see GitHub's documentation on [fine-grained personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens).

## GitHub Pages

To publish the app:

1. Open the repository **Settings**.
2. Select **Pages** in the sidebar.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select the `main` branch and the `/ (root)` folder.
5. Click **Save**.

The site will be available at:

`https://cha0s-mnk.github.io/My-Agenda/`
