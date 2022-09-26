# Typescript + Svelte + Sass + Vite library template
Clone this template to easily get started creating a new [ESM](https://nodejs.org/api/esm.html) package template that uses [Typescript](https://www.typescriptlang.org/docs/) for coding, [Svelte](https://svelte.dev/) for reactive UI, [Sass](https://sass-lang.com/) to enhance CSS, and [Vite](https://vitejs.dev/) as the bundler tool

New to front-end web development? Check out our [Web Developer Guide](https://gambitgames.gitbook.io/web-dev-guide/) for the basics on each tool.

Choose this template when you need to create a new reactive UI component.

---------------------------
HOW TO CLONE
---------------------------
- Visit this package on [Github](https://github.com/GambitGamesLLC/front-end-web-template), press the "Use This Template" button at the top right.

- Fill out the details for your new project like normal

- Open the ```package.json``` file and change the ```"name"``` to be the same as what you named your repository.

- Open your VSCode terminal and run ```pnpm install``` to install the necessary packages to your node_modules folder (this is not uploaded to your github repository)

---------------------------
HOW TO USE THIS TEMPLATE
---------------------------
- This template uses [Typescript](https://www.typescriptlang.org/docs/), a superset of the Javascript language.

- Typescript allows you to add type definitions for a better debugging and intellisense experience for anyone using your library. If your unfamiliar with Typescript, you can still write normal Javascript in a .ts (Typescript) file. 

- When making builds, your typescript code will become Javascript, so don't worry about compatability.

- Your library's entry point for logic is the ```./lib/main.ts``` file. Write your library logic starting from that file.

- The ```./test.js``` file at the project root is used to load up and test your package. This script is loaded by the main entrypoint when testing (```./index.html```).

---------------------------
HOW TO TEST YOUR LIBRARY
---------------------------
- To test your library, open the VSCode terminal and run the ```pnpm run dev``` command and Ctrl+Left Click on the browser link that is generated by Vite in your terminal window. 

- This will open your web browser to your ```index.html``` page, which automatically runs the logic within ```test.js```, and by default imports your ```main.ts``` module.

- Any changes you make to your code will automatically compile and run in the browser link that Vite generated for you.

- Please note that hot module replacement does not function properly with Svelte Reactive UI + Vite and has been disabled. Your code is still testable, but the state of your variables will refresh from scratch everytime you save a file.

---------------------------
HOW TO BUILD YOUR LIBRARY
---------------------------
- To build your library for distribution, open the VSCode terminal and run the ```pnpm run build``` command. 

- This will generate a ```dist``` folder containing your HTML/CSS/JS files, type definitions, sourcemaps, and other asset files.

- Make sure your ```dist``` folder gets uploaded to your github repo.

- It should already be set properly, but make sure your ```.gitignore``` is allowing files in the ```dist``` folder to get uploaded to your repository

----------------------------
HOW TO IMPORT YOUR LIBRARY
----------------------------
- Once you have written you library, built it, and uploaded it to github. Make a new project to test it.

- In this new project's VSCode terminal window, run the ```pnpm install URL```, just replace the ```URL``` variable at the end with the web url to the github repository for the library package you created.

- EX: ```pnpm install @github:Organization/PackageName```

- This will add the library package to your ```node_modules``` folder, ready to be used by your new project. 

- To import your code into your new projects Javascript or Typescript, use the ESM Import command

```import * as Package from "package-name"```

- Replace the ```package-name``` with the name you wrote in the ```package.json``` file of your library

- Your comments and variable type definitions should appear in the VSCode intellisense as expected

- Your variables and functions from your library are now accessible within the ```Package``` variable

-----------------------------------------------------
HOW TO SET A PACKAGE AS AN EXTERNAL DEPENDENCY
-----------------------------------------------------
- An external dependency is a package you want to use in your library, but you don't necessarily want to bundle that package's code together with your library

- This will prevent the other package's code from appearing in your ```dist``` folder after ```pnpm run build``` is called from the VSCode terminal.

- To add an external dependency, open the ```vite.config.js``` file and add the name of the package you wish to turn into an external dependency to the ```external[""]``` array.

- EX: ```external["@babylonjs/core"]```

- This is mostly useful for very large packages (like @babylonjs/core, Svelte, React, Vue, etc). In these cases an actual application will import those large packages themselves, so you don't need to include them with your library build.

-----------------------------------------------------
HOW TO IMPORT A PACKAGE AS A DEVELOPER DEPENDENCY
-----------------------------------------------------
- Developer dependencies are packages that can be used while working in VSCode, but they won't exist when ```pnpm run build``` is called, so they cannot be used by any code that will be part of the ```dist``` folder.

- This can be useful for importing packages that help test your library in your ```index.html``` or ```test.js``` file, but aren't important otherwise.

-----------------------------------------------------
HOW TO REMOVE A DEPENDENCY
-----------------------------------------------------
- To remove a package dependency from your library, run the ```pnpm remove package-name``` command in your VSCode terminal. Where ```package-name``` is the name of the package you wish to remove.

- This works for all package imports. Including developer dependencies.

- This command will not automatically remove the name of the package from the ```vite.config.js``` file if you previously added it to the ```external[""]``` array. You will need to manually remove those yourself.
