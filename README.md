# React PDF Starter Toolkit in Docusaurus and TypeScript

Welcome to the React PDF Starter Toolkit! This repository provides a comprehensive guide on integrating React PDF with Docusaurus and TypeScript. It showcases how React PDF can be integrated and rendered as part of a React.js project.

## Table of Contents

- [Usage](#usage)
  - [Project Setup](#project-setup)
  - [Running the Example Project](#running-the-example-project)
- [Examples](#examples)

## Usage

### Project Setup

1. **Clone the Repository**: If you haven't already, clone the repository and navigate into the project directory.

   ```bash
   git clone https://github.com/pdf-viewer-react/starter-rp-docusaurus-ts.git
   cd starter-rp-electron-ts
   ```

2. **Install Dependencies**: Install the necessary dependencies using npm, yarn, pnpm or bun.

   ```bash
   npm install
   # or
   yarn install
   # or
   pnpm install
   # or
   bun install
   ```

### Running the Example Project

This repository includes an example project to demonstrate React PDF in action.

1. **Start the Development Server**: Use the following command to start the development server

```bash
   npm run start
   # or
   yarn start
   # or
   pnpm run start
   # or
   bun run start
   ```
   
By default, the dev server runs on `http://localhost:3000`.

### Using the React PDF Component

Once the example project is running, you can explore the source code to see how the React PDF component is integrated. Here is a brief overview:

1.  **Import the component**: Import the desired React PDF component into your codes

```tsx
import {
  RPDefaultLayout,
  RPLayoutProps,
  RPPages,
  RPProvider,
  RPProviderProps,
} from "@pdf-viewer/react";
import React, { type FC } from "react";

interface IProps {
  showToolbar: boolean;
  providerProps: Omit<RPProviderProps, "src">;
  defaultLayoutProps: RPLayoutProps;
}

const DEFAULT_PDF_URL =
  "https://cdn.codewithmosh.com/image/upload/v1721763853/guides/web-roadmap.pdf";

const AppPdfViewer: FC<Partial<IProps>> = (props) => {
  const { showToolbar = true, providerProps, defaultLayoutProps } = props;
  return (
    <div>
      <RPProvider src={DEFAULT_PDF_URL} {...providerProps}>
        {showToolbar ? (
          <RPDefaultLayout {...defaultLayoutProps}>
            <RPPages />
          </RPDefaultLayout>
        ) : (
          <div style={{ width: "100%", height: "550px" }}>
            <RPPages />
          </div>
        )}
      </RPProvider>
    </div>
  );
};

export default AppPdfViewer;
```

2. **Use the component in the page**: Add the React PDF component to your page

```tsx
import type { ReactNode } from "react";
import useDocusaurusContext from "@docusaurus/useDocusaurusContext";
import { RPConfig } from "@pdf-viewer/react";
import AppPdfViewer from "../components/AppPdfViewer";

export default function Home(): ReactNode {
  const { siteConfig } = useDocusaurusContext();
  return (
    <RPConfig>
      <div className="container">
        <h1>{siteConfig.title}</h1>
        <br />
        <h2>Default Toolbar</h2>
        <AppPdfViewer />
        <br />
        <h2>Without Toolbar</h2>
        <AppPdfViewer
          showToolbar={false}
          defaultLayoutProps={{
            style: { width: "100%", height: "550px" },
          }}
        />
        <br />
        <h2>Mobile</h2>
        <AppPdfViewer
          defaultLayoutProps={{
            style: { width: "500px" },
          }}
        />
      </div>
    </RPConfig>
  );
}
```

## Examples

For more examples, please refer to the `src/pages/index.tsx` file in this repository:

- Default Toolbar
- Without Toolbar
- Mobile View

_Remark: If you would like more examples, feel free open an issue._

For more configurations, please check the [documentation](https://docs.react-pdf.dev) site.

## Meta

- Homepage: [https://www.react-pdf.dev](https://www.react-pdf.dev)
- Docs: [https://docs.react-pdf.dev](https://docs.react-pdf.dev)

---

Thank you for using React PDF! We hope this toolkit helps you build amazing React.js applications. If you have any questions or need further assistance on this example, please feel free to open an issue. Happy coding!