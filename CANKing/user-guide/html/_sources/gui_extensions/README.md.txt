**Kvaser CanKing GUI Extensions SDK v7.5.0**

***

# Kvaser CanKing GUI Extensions SDK

## Introduction

The purpose with this package is to help developers to create user interface extensions for the Kvaser CanKing bus analysis tool.

Kvaser CanKing is a free of charge, general-purpose CAN and LIN bus analysis software that is compatible with all Kvaser CAN
and LIN interfaces and the Kvaser virtual CAN bus. It's available on Windows (x64) and Linux (x64 and ARM).

There are a lot of functionality already included in the base version of CanKing, but it is also possible to extend the
functionality and the user interface by creating extensions.

An extension is developed as a stand-alone [React](https://react.dev/) web application. The web application will be hosted
by an express web server inside CanKing and it will be mounted into the CanKing user interface using a webview element.

When an extension is mounted into CanKing, then a preload script will run to inject inter-process communication (IPC)
functions. These functions will make it possible for the extension to communicate with CanKing to get information and to
interact with the CAN/LIN bus.

The IPC functions are accessible by importing different modules from the @kvaser/canking-api package.

To get or subscribe on CanKing data there are different React hooks to be used. All these can be found in the hooks module.

```tsx
import { useUserSetting, useMeasurementSetup } from '@kvaser/canking-api/hooks';

...

const userSettings = useUserSettings();
const measurementSetup = useMeasurementSetup();
```

To interact with CanKing there are different functions that can be imported from the ipc module.

```tsx
import { sendCanMessage } from '@kvaser/canking-api/ipc';

...

sendCanMessage(channelId, frameId, data, flags);
```

The @kvaser/canking-api package also includes some React components that you can use, e.g. there is a component for selecting
channel.

```tsx
import { CanChannelSelectControl } from '@kvaser/canking-api/controls';

...

function WorkspaceView() {
  const [channelId, setChannelId] = useState('');
  return (
    <CanChannelSelectControl
      channelIdentifier={channelId}
      onChannelIdentifierChange={setChannelId}
      hideSectionControl
    />
  );
}
```

## SDK version changes

Version-specific SDK changes and migration notes are documented in [CHANGELOG.md](_media/CHANGELOG.md).

## Prerequisites

Before creating a new CanKing Extension the following softwares need to be installed.

- Node.js: <https://nodejs.org/>
- Kvaser CanKing: <https://kvaser.com/canking/>
- Kvaser Drivers: <https://resources.kvaser.com/7330130980013/latest/kvaser_drivers_setup.exe>

You will also need an IDE (Integrated Development Environment) to edit and debug your code. We recommend that you're using
[Visual Studio Code](https://code.visualstudio.com/).

With Visual Studio Code you might also want to install these extensions to help you with code formatting and code analysing:

- [ESLint (dbaeumer.vscode-eslint)](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Prettier - Code formatter (esbenp.prettier-vscode)](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [EditorConfig for VS Code (editorconfig.editorconfig)](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)

## Generate a new CanKing Extension project

The simplest way to create a new CanKing Extension project is to use the script that is included in the
[@kvaser/create-canking-extension](https://www.npmjs.com/package/@kvaser/create-canking-extension) package. The script is
used like this:

```bash
npm create @kvaser/canking-extension@latest
```

Then follow the prompts.

You can also specify a project name via a command line argument.

```bash
npm create @kvaser/canking-extension@latest my-ck-extension
```

This command will create a new project in a new folder with the same name as the specified project name (my-ck-extension).
You can use `.` for the project name to scaffold your project in the current directory.

The command above will create a folder structure like this:

```text
my-ck-extension
│   .gitignore
│   .prettierrc
│   eslint.config.mjs
│   index.html
│   package.json
│   tsconfig.app.json
│   tsconfig.json
│   tsconfig.node.json
│   vite.config.ts
│
├───.vscode
│       launch.json
│
└───src
    │   App.tsx
    │   cjk-fonts.css
    │   global.css
    │   main.tsx
    │   vite-env.d.ts
    │
    ├───assets
    │       icon.png
    │
    └───WorkspaceView
            index.tsx
```

The project follows a similar file structure as the one that is created for a [Vite](https://vite.dev/) project created
using the react-ts template. There are some extra information added to the package.json file that are needed for CanKing and
the src files are modified to be used inside CanKing.

The my-ck-extension/src/WorkspaceView/index.tsx file is the file that includes the React component that will be mounted into
CanKing, so this is the file you should implement to create your extension.

## Develop a CanKing Extension

To match the CanKing look and feel, it's recommended to use Material UI components when applicable,
<https://mui.com/material-ui/all-components/>.

The WorkspaceView React component (src/WorkspaceVew/index.tsx) will be displayed when the extension is loaded into CanKing,
so this is the component that should be implemented to implement the extension.

To run the extension from command line enter:

```bash
npm run start
```

To run the extension using Visual Studio Code debugger:

- Select 'Run and Debug' or press Ctrl+Shift+D
- Select the configuration named 'Debug'
- Click on 'Start Debugging' or press F5

To run a production build of the extension you can enter this command:

```bash
npm run startpreview
```

If you need more information and help about how to interact with CanKing then you can run this command:

```bash
npx @kvaser/canking-api --help
```

This will open up a help file in your web browser.

## Package and Install a CanKing Extension

To package your extension for distribution you should run this command from the command line:

```bash
npm pack
```

This command will create a tarball file in the root folder of your project called:

```text
<project-name>-<version>.tgz
```

This tarball can then be installed in CanKing using the head menu 'More'->'Extensions'->'Install'.
