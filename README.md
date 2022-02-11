# workspace-demo

npm has a feature for managing multiple packages in mono repo using workspaces. 
- 

Workspaces are defined in package.json as follow 

```
{
  "name": "workspace-demo",
  "scripts": { ... },
  "workspaces": [
    "app", "cdk", "common ...
  ]
}
```

We then can define script at the root that will look for scripts in the packages in the workspace. 

i.e root package.json

```
{
...
  scripts: {
     "build:all": "npm run build --workspaces --if-present",
  }
  ...
}
```

The above script will look for all build script in app, cdk and common folders.

### Workspace Scripts and Useful Commands

* ``npm run build:all``: Build all packages in the workspace
* ``npm run clean:all``: this will run the clean script for all packages. i.e removes node_modules and cdk.out folder for cdk  
* ``npm run test:all``: Test all

``npm install`` at root will download all dependency for each folder.

Please read [npm workspace](https://docs.npmjs.com/cli/v7/using-npm/workspaces) for more information



