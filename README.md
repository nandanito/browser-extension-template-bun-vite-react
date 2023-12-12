# Browser Extension Template with Bun, Vite and TypeScript

![GitHub license](https://img.shields.io/github/license/nandanito/browser-extension-template-bun-vite-react)
![Bun](https://img.shields.io/badge/bun-1.x-blue)
![React](https://img.shields.io/badge/react-18.x-blue)
![TypeScript](https://img.shields.io/badge/typescript-5.x-blue)
![Tailwind CSS](https://img.shields.io/badge/tailwindcss-3.x-blue)
![Vite](https://img.shields.io/badge/vite-5.x-blue)

This template serves as the boilerplate code to develop browser extension using [Bun](https://bun.sh/) & [Vite](https://vitejs.dev/) for modular tooling for Typescript development, [React](https://react.dev/) for the user interface and [Tailwind](https://tailwindcss.com/) for flexible styling.

The main aim is to offer the simple template to get started with the browser extension using Bun, an all-in-one JavaScript runtime & toolkit.

The project is based upon [chrome-extension-boilerplate-react-vite-typescript](https://github.com/himalaya0035/chrome-extension-boilerplate-react-vite-typescript/) and [create-chrome-ext](https://github.com/guocaoyi/create-chrome-ext).

## Features

- 🚀 Speedy development using [Bun](https://bun.sh/) integrated toolkit and Vite's fast HMR
- 🛠️ Automated extension manifest file generation using [CRXJS Vite-Plugin](https://crxjs.dev/vite-plugin)
- ⚛️ React-powered user interface along with [Tailwind](https://tailwindcss.com/) for quick & easy styling
- 🗃️ Out of the box support for Popup, Options, Background Script, ConctentScript, DevTools, NewTab and SidePanel (use @crxjs/vite-plugin 2.x-beta)

## Prerequisites

- Node.js LTS or higher
- Bun

## Getting Started

Follow along with the following steps to get the template running:

1. Clone the repository

```sh
git clone https://github.com/nandanito/browser-extension-template-bun-vite-react.git
```

2. Navigate to the project folder:

```sh
cd browser-extension-template-bun-vite-react
```

3. Chane `name` anbd `description` in the `package.json` file

4. Install dependencies:

```sh
bun install
```

5. Run the development server

```sh
bun run dev
```

6. Test the extension in browser:

- for Chrome:

  - Open in the browser: `chrome://extensions`
  - Turn on the option `Developer Mode`
  - Find and Click `Load unpacked extension`
  - Select the `dist` folder in the project directory

- for Firefox: WIP

7. Start with the development by editing/customizing the `index.tsx` files in the respective directories for background, contentscript, options, popup, etc.

8. Build for production:

When ready for the production, run the following:

```sh
bun run build
```

The `dist` folder will be created, which can be packaged to distribute the extension.

## Contributing

Any sort of contributions are welcome! If you encounter any issues or have ideas for improvements, feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

## Support

⭐️ If you find this boilerplate helpful, consider giving it a star on [GitHub](https://github.com/nandanito/browser-extension-template-bun-vite-react).

---

If you have any questions, feel free to reach out to me!

**Disclaimer:** This project was created by [Nandan](https://github.com/nandanito/) to address the lack of getting started resources for building browser extensions, esp., with Bun. It is not officially endorsed by any of the mentioned technologies or organizations.

---
