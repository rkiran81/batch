# Angular Nx Monorepo Example

### Recreate this monorepo starting out with the angular-microfrontend-example project

```shell
cp -R angular-microfrontend-example angular-monorepo
cd angular-monorepo
npx nx@latest init --integrated
cp ../angular-microfrontend-example/angular.json ./
# The following steps are manual unfortunately!

# Change tsconfig.base.json @shared paths => Change “project” to “libs” and change “dist/shared” to “dist/libs/shared”
# In all project webpack.config.js files => Change module paths to remove the “projects” path - change these to “apps”
# Change angular.json file => Alter “projects” paths used everywhere to either "apps" or "libs" in the angular.json
# Change all project.json files => Change all “project” path references to apps or libs in the app and library project.json files
# Remove the “projects” path in the tailwind.config.js file

cp tsconfig.base.json tsconfig.json # (Module federation library needs this)

# You're ready! To start the app(s) run:
npx nx run-many  --target serve --all
```

## License

Apache 2.0, see [LICENSE](LICENSE).
