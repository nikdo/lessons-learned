# Configuration

There are **two types of application configuration**:

1. Compile-time: hardcoded into the compiled code
2. Runtime: read during runtime from somewhere

Environment variables in Create React App are counter-intuitively [a compile-time configuration](https://create-react-app.dev/docs/adding-custom-environment-variables). They are injected at build time.

The Twelve-Factor App suggests [strict separation of config from code](https://12factor.net/config) by storing configuration to environment variables that are read on runtime.

There is also a third option: fetch configuration asynchronously. But [it has severe downsides](https://github.com/facebook/create-react-app/issues/578#issuecomment-278178929) and should be avoided. Remember MCO?

## Configuration security

Because React app runs in the browser, **there is nothing like secret variable**. Both compile-time and runtime variables are present in some files served to the browser and can be read by anyone. Storing secrets there is a major security breach.

## React runtime configuration

For having React application runtime configuration, there are several approaches.

1. [Injecting it into index.html](https://create-react-app.dev/docs/title-and-meta-tags/#injecting-data-from-the-server-into-the-page). Server replaces some placeholder with the configuration.
2. [Injecting it into JavaScript bundle](https://github.com/facebook/create-react-app/issues/578#issue-174968572) as it is done by Heroku [create-react-app-buildpack](https://github.com/mars/create-react-app-buildpack). The server replaces variables in the bundle by its own values.
3. [Injecting it into separate JavaScript file](https://github.com/facebook/create-react-app/issues/578#issuecomment-300651519) that is then loaded into index.html before the bundle. The server generates this file from the configuration. This is a modification of the approach #4 below. Also suggested in [this article](https://www.freecodecamp.org/news/how-to-implement-runtime-environment-variables-with-create-react-app-docker-and-nginx-7f9d42a91d70/). The downside is that this is yet another file to be loaded by the client.

In all these three scenarios, it is preferred for the server to keep the configuration in environment variables.

4. [Having a static JavaScript file](https://github.com/facebook/create-react-app/issues/578#issuecomment-277843310) that is loaded into index.html before the bundle. The server just serves this file that can be different for different environments. Also suggested in [this article](https://dev.to/matt_catalfamo/runtime-configurations-with-react-22dl). The downside is that this is yet another file to be loaded by the client.
