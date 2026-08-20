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

Only the repository owner or a GitHub collaborator with write permission can save directly to this repository. A normal GitHub login is not enough by itself: the app checks the account's repository write permission before it creates a commit. Other people can read the agenda but cannot edit `agenda.json` in this repository.

Every successful save is a normal GitHub commit, so do not put private or sensitive information in the agenda.

## One-time GitHub sync setup

The app uses a GitHub App Device Flow. It never asks for or stores your GitHub password. The access token is kept only in the current browser session and may need to be renewed on another device or after it expires.

1. In GitHub, open **Settings → Developer settings → GitHub Apps → New GitHub App**.
2. Give it a name such as **My Agenda Sync** and use `https://cha0s-mnk.github.io/My-Agenda/` as the Homepage URL.
3. Enable **Device Flow**.
4. Under **Repository permissions**, set **Contents** to **Read and write**. Leave **Metadata** at its required read-only setting.
5. Install the app on **My-Agenda only**.
6. Copy the app's public **Client ID**. Do not use the App ID, client secret, or an access token.
7. Open the agenda site, expand **One-time GitHub sync setup**, paste the Client ID, and select **Save client ID**.
8. Select **Log in with GitHub**, open the displayed device link, and enter the displayed code.

After that, **Save to GitHub** checks write permission and commits the current agenda to `agenda.json`. **Refresh from GitHub** replaces the current browser copy with the latest public version.

## GitHub Pages

To publish the app:

1. Open the repository **Settings**.
2. Select **Pages** in the sidebar.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select the `main` branch and the `/ (root)` folder.
5. Click **Save**.

The site will be available at:

`https://cha0s-mnk.github.io/My-Agenda/`
