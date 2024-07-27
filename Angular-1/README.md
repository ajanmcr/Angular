# Angular1

## Basic File Structure

- `.editorconfig`: Configuration for code editors. EditorConfig helps maintain consistent coding styles for multiple developers working on the same project across various editors and IDEs.
- `.gitignore`: Specifies intentionally untracked files that Git should ignore.
- `README.md`: Documentation of the workspace.
- `angular.json`: the root level of an Angular workspace provides workspace-wide and project-specific configuration defaults. These are used for build and development tools provided by the Angular CLI.
  - a few properties configure the workspace and a `projects` section contains the remaining per-project configuration options.
  - `version`: The configuration-file version.
  - `newProjectRoot`: Path where new projects are created through tools like `ng generate application` or `ng generate library`. Path can be absolute or relative to the workspace directory. Defaults to `projects`, i.e all the `ng generate application` are added to `projects` array.
  - `projects`: Contains a subsection for each application or library in the workspace, with project-specific configuration options. - `root`: The root directory for this project's files, relative to the workspace directory. Empty for the initial application, which resides at the top level of the workspace.
  - `projectType`: One of "application" or "library" An application can run independently in a browser, while a library cannot.
  - `sourceRoot`: The root directory for this project's source files.
  - `prefix`: A string that Angular prepends to selectors when generating new components, directives, and pipes using ng generate. Can be customized to identify an application or feature area.
  - `architect`: Configuration defaults for Architect builder targets for this project.
    - `build`: Configures defaults for options of the `ng build` command.
    - `serve`: Overrides build defaults and supplies extra serve defaults for the `ng serve` command. Besides the options available for the `ng build` command, it adds options related to serving the application.
- `package.json`: Configures npm package dependencies that are available to all projects in the workspace.
- `package-lock.json`: lock.json Provides version information for all packages installed into `node_modules` by the npm client.
- `tsconfig.json`: The base TypeScript configuration for projects in the workspace. All other configuration files inherit from this base file.
- `tsconfig.app.json`: Application-specific TypeScript configuration, including Angular compiler options.
- `tsconfig.spec.json`: TypeScript configuration for application tests.
- `src`: Source files for the root-level application project.

  - `assets`: static resources like images, icons, text files. Publicly accessible.
  - `favicon.ico`: An icon to use for this application in the bookmark bar.
  - `index.html`: The main HTML page that is served when someone visits your site. The CLI automatically adds all JavaScript and CSS files when building your app, so you typically don't need to add any `script` or `link` tags here manually.
  - `main.ts`: The main entry point for your application.
  - `styles.css`: global CSS styles to the application
  - `app/`: Contains the component files in which your application logic and data are defined.

    - `app.config.ts`: Defines the application configuration that tells Angular how to assemble the application. As you add more providers to the app, they should be declared here. Only generated when using the --standalone option
    - `app.component.ts`: Defines the application's root component, named AppComponent. The view associated with this root component becomes the root of the view hierarchy as you add components and services to your application.
    - `app.component.html`: Defines the HTML template associated with AppComponent.
    - `app.component.css`: Defines the CSS stylesheet for AppComponent.
    - `app.component.spec.ts`: Defines a unit test for AppComponent.
    - `app.module.ts`:Defines the root module, named AppModule, that tells Angular how to assemble the application. Initially declares only the AppComponent. As you add more components to the app, they must be declared here. Only generated when using the --standalone false option.
    - `app.routes.ts`: Defines the application's routing configuration.

## Execution Flow

- `angular.json`: the builder looks for `main` attribute in the `options` object, under `build` object, which tells the builder about the entry point of the application.
- `main.ts`: This file acts as the entry point of the application. `main.ts` helps in creating the browser environment for the application to run. In case entry point needs to point to different file then filename should be modified in `angular.json` & `tsconfig.app.json`. After this, `main.ts` file calls the function `bootstrapModule`(AppModule) which tells the builder to bootstrap the app.
- `app.module.ts`: From the main.ts file, it is very clear that we are bootstrapping the app with `AppModule`. This is the module, created with the `@NgModule` decorator, which has declarations of all the components we are creating within the app module so that angular is aware of them, and provide bootstrapping component.
- `app.component.ts`: Defines the application's root component, named AppComponent. The view associated with this root component becomes the root of the view hierarchy as you add components and services to your application. And builder replaces the selector of this component with the html template.
- `index.html`: When this angular app is served and opened in the browser, the scripts injection is done by the compiler. these scripts are:
  - `runtime.js`: webpack runtime file
  - `polyfills.js`: compatible with old browser
  - `main.ts`: application code compiled to JavaScript
  - `vendor.js`: contains angular core library & third party library.
  - `style.js`: style.css is bundled to style.js & injected to index.html

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.0.0.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
