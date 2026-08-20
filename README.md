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
- Generate one copyable prompt for ChatGPT to polish the complete agenda in concise British English.
- Load the public `agenda.json` automatically when the app opens.
- Save the current agenda to GitHub with one click, creating a public commit.
- Keep a local browser copy for fast editing and offline fallback.
- Import an agenda from JSON.

## Public-data model

This repository is public. Anyone can read the agenda, its task text, and its complete commit history. Anyone may also copy or fork the repository.

Only the repository owner or a GitHub collaborator with write permission can save directly to this repository. The app checks the token's repository write permission before it creates a commit. Other people can read the agenda but cannot edit `agenda.json` in this repository.

Every successful save is a normal GitHub commit, so do not put private or sensitive information in the agenda.

## Current sync pipeline

The app uses GitHub as the shared source of truth:

1. When the page opens, it loads the latest public `agenda.json` from the `main` branch.
2. Adding, editing, completing, deleting, importing, or refreshing tasks updates the current browser copy first.
3. **Save to GitHub** checks the connected token and confirms that it has write permission for `My-Agenda`.
4. The app reads the current file version, then updates `agenda.json` through GitHub's Contents API, creating a new public commit.
5. Another device can load that commit automatically or use **Refresh from GitHub**.

The app does not use a webhook, GitHub App, Device Flow, client ID, or client secret. GitHub's REST API is used only for the authenticated save and permission check; public agenda loading does not require authentication.

## One-time GitHub sync setup

Because this is a static GitHub Pages site, it uses a fine-grained personal access token instead of a browser-based GitHub login. The app never receives your GitHub password. The token is masked and kept only in the current browser tab.

1. Open GitHub's [new fine-grained token page](https://github.com/settings/personal-access-tokens/new).
2. Give the token a name such as **My Agenda Save** and choose an expiry date.
3. Under **Repository access**, choose **Only select repositories**, then select **My-Agenda**.
4. Under **Repository permissions**, set **Contents** to **Read and write**. Leave other permissions at their defaults.
5. Generate the token and copy it immediately. GitHub will not show the complete token again.
6. Open the agenda site, expand **One-time GitHub sync setup**, paste the token, and select **Connect token**.
7. Select **Save to GitHub** to create a public commit in `agenda.json`.

> **Important:** GitHub displays the complete token only once. If you leave the token-creation page before copying it, the token cannot be recovered; generate a new token instead. Never put the token in this repository or send it in a message.

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
