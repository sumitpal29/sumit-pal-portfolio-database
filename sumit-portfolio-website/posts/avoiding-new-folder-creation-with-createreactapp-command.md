---
title: Avoiding New Folder Creation with the create-react-app Command
slug: avoiding-new-folder-creation-with-createreactapp-command
createdAt: '2026-05-02T15:47:32.177Z'
updatedAt: '2026-05-02T19:45:29.748Z'
metadata:
  title: >-
    Avoiding New Folder Creation with the create-react-app CommandAvoiding New
    Folder Creation with the create-react-app CommandAvoiding New Folder
    Creation with the create-react-app Command
  description: ''
  heroImage: 'https://i.imgur.com/Y4r8lLR.png'
  draft: false
  publishedAt: '2023-09-11T15:47:00.000Z'
description: ''
heroImage: 'https://i.imgur.com/Y4r8lLR.png'
draft: false
publishedAt: '2023-09-10T23:17:00.000Z'
---
The create-react-app command is a powerful tool for setting up React projects, complete with essential tools and even TypeScript support.

According to official documentation, to initiate a new React project within a folder named "my-app," you'd use:

```json
npx create-react-app my-app
```

This command creates a new folder named "my-app" and populates it with all the necessary project files. However, there are instances where we want to avoid creating a new folder. Perhaps we already have a designated project folder and we would like the files to be generated there.

In such cases, navigate to the desired folder and employ the following command:

```json
npx create-react-app .
```

The dot (.) here is crucial. It instructs the command not to create a new folder, ensuring that the project files are generated directly within the current directory.
