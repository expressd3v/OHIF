<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<div align="center">
  <h1>OHIF Medical Imaging Viewer</h1>
  <p><strong>The OHIF Viewer</strong> is a zero-footprint medical image viewer provided by the Open Health Imaging Foundation (OHIF).</p>
</div>

## About

The OHIF Medical Imaging Viewer is for viewing medical images. It can retrieve
and load images from most sources and formats; render sets in 2D, 3D, and
reconstructed representations; allows for the manipulation, annotation, and
serialization of observations; supports internationalization, OpenID Connect,
offline use, hotkeys, and many more features.

Almost everything offers some degree of customization and configuration. If it
doesn't support something you need, we accept pull requests and have an ever
improving Extension System.


## Quick Start Deployment
In practice, this is as simple as:

```js
window.config = {
  routerBasename: '/',
  servers: {
    dicomWeb: [
      {
        name: 'DCM4CHEE',
        qidoRoot: 'https://server.dcmjs.org/dcm4chee-arc/aets/DCM4CHEE/rs',
        wadoRoot: 'https://server.dcmjs.org/dcm4chee-arc/aets/DCM4CHEE/rs',
        qidoSupportsIncludeField: true,
        imageRendering: 'wadors',
        thumbnailRendering: 'wadors',
      },
    ],
  },
};
```

- Install the viewer:
  `window.OHIFViewer.installViewer(window.config);`

## Developing

### Requirements

- [Yarn 1.17.3+](https://yarnpkg.com/en/docs/install)
- [Node 10+](https://nodejs.org/en/)
- Yarn Workspaces should be enabled on your machine:
  - `yarn config set workspaces-experimental true`

### Getting Started
`yarn install` to restore dependencies and link projects

#### To Develop

_From this repository's root directory:_

```bash
# Enable Yarn Workspaces
yarn config set workspaces-experimental true

# Restore dependencies
yarn install
```

## Commands

These commands are available from the root directory. Each project directory
also supports a number of commands that can be found in their respective
`README.md` and `project.json` files.

| Yarn Commands                | Description                                                   |
| ---------------------------- | ------------------------------------------------------------- |
| **Develop**                  |                                                               |
| `dev` or `start`             | Default development experience for Viewer                     |
| `dev:project <package-name>` | Replace with `core`, `ui`, `i18n`, `cornerstone`, `vtk`, etc. |
| `test:unit`                  | Jest multi-project test runner; overall coverage              |
| **Deploy**                   |                                                               |
| `build`\*                    | Builds production output for our PWA Viewer                   |
| `build:package`\*            | Builds production `commonjs` output for our Viewer            |
| `build:package-all`\*        | Builds commonjs bundles for all projects                      |

\* - For more information on our different builds, check out our [Deploy
Docs][deployment-docs]

## Projects

The OHIF Medical Image Viewing Platform is maintained as a
[`monorepo`][monorepo]. This means that this repository, instead of containing a
single project, contains many projects. If you explore our project structure,
you'll see the following:

```bash
.
├── extensions              #
│   ├── _example            # Skeleton of example extension
│   ├── cornerstone         # 2D images w/ Cornerstone.js
│   ├── dicom-html          # Structured Reports as HTML in viewport
│   ├── dicom-microscopy    # Whole slide microscopy viewing
│   ├── dicom-pdf           # View DICOM wrapped PDFs in viewport
│   └── vtk                 # MPR and Volume support w/ VTK.js
│
├── platform                #
│   ├── core                # Business Logic
│   ├── i18n                # Internationalization Support
│   ├── ui                  # React component library
│   └── viewer              # Connects platform and extension projects
│
├── ...                     # misc. shared configuration
├── lerna.json              # MonoRepo (Lerna) settings
├── package.json            # Shared devDependencies and commands
└── README.md               # This file
```

Want to better understand why and how we've structured this repository? Read
more about it in our [Architecture Documentation][ohif-architecture].


## License

MIT © EXPRESSD3V
