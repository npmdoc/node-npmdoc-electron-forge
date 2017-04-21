# npmdoc-electron-forge

#### api documentation for  electron-forge (v2.10.0)  [![npm package](https://img.shields.io/npm/v/npmdoc-electron-forge.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-electron-forge) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-electron-forge.svg)](https://travis-ci.org/npmdoc/node-npmdoc-electron-forge)

#### A complete tool for building modern Electron applications

[![NPM](https://nodei.co/npm/electron-forge.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/electron-forge)

- [https://npmdoc.github.io/node-npmdoc-electron-forge/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-electron-forge/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-electron-forge/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-electron-forge/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-electron-forge/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-electron-forge/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "electron-forge",
    "version": "2.10.0",
    "description": "A complete tool for building modern Electron applications",
    "repository": "https://github.com/electron-userland/electron-forge",
    "main": "dist/api/index.js",
    "bin": {
        "electron-forge": "dist/electron-forge.js",
        "forge": "dist/electron-forge.js",
        "electron-forge-vscode-nix": "script/vscode.sh",
        "electron-forge-vscode-win": "script/vscode.cmd"
    },
    "scripts": {
        "build": "gulp build",
        "precommit": "npm run lint",
        "commit": "git-cz",
        "docs": "esdoc",
        "install": "node tabtab-install.js",
        "lint": "eslint src test gulpfile.babel.js",
        "prepublish": "gulp build",
        "pretest": "gulp build",
        "test": "npm run lint && npm run test-all",
        "test-coverage": "npm run lint && npm run test-all-coverage",
        "test-all": "mocha test/**/*_spec*.js --compilers js:babel-register --timeout=300000",
        "test-fast": "mocha test/**/*_spec.js --compilers js:babel-register --timeout=10000",
        "test-all-coverage": "cross-env NODE_ENV=test nyc npm run test-all",
        "test-fast-coverage": "cross-env NODE_ENV=test nyc npm run test-fast",
        "release:patch": "changelog -p && node ci/fix-changelog.js && git add CHANGELOG.md && git commit -m \"updated CHANGELOG.md\" && npm version patch && git push origin && git push origin --tags",
        "release:minor": "changelog -m && node ci/fix-changelog.js && git add CHANGELOG.md && git commit -m \"updated CHANGELOG.md\" && npm version minor && git push origin && git push origin --tags",
        "release:major": "changelog -M && node ci/fix-changelog.js && git add CHANGELOG.md && git commit -m \"updated CHANGELOG.md\" && npm version major && git push origin && git push origin --tags",
        "watch": "gulp watch",
        "watch-link": "nodemon --watch src --exec \"npm link\""
    },
    "author": "Samuel Attard",
    "license": "MIT",
    "devDependencies": {
        "babel-eslint": "^7.0.0",
        "babel-plugin-istanbul": "^4.0.0",
        "babel-plugin-syntax-async-functions": "^6.13.0",
        "babel-plugin-transform-async-to-module-method": "^6.16.0",
        "babel-plugin-transform-runtime": "^6.15.0",
        "babel-preset-es2015": "^6.16.0",
        "chai": "^3.5.0",
        "chai-as-promised": "^6.0.0",
        "chai-fetch-mock": "^1.0.0",
        "commitizen": "^2.8.6",
        "coveralls": "^2.11.15",
        "cross-env": "^4.0.0",
        "cz-customizable": "4.0.0",
        "esdoc": "^0.5.1",
        "esdoc-importpath-plugin": "^0.1.0",
        "eslint": "^3.7.1",
        "eslint-config-airbnb-base": "^8.0.0",
        "eslint-plugin-import": "^2.2.0",
        "eslint-plugin-mocha": "^4.8.0",
        "fetch-mock": "^5.8.1",
        "generate-changelog": "^1.0.2",
        "gulp": "^3.9.1",
        "gulp-babel": "^6.1.2",
        "mocha": "^3.2.0",
        "nodemon": "^1.11.0",
        "nyc": "^10.0.0",
        "proxyquire": "^1.7.10",
        "sinon": "^2.1.0"
    },
    "babel": {
        "env": {
            "test": {
                "plugins": [
                    "istanbul"
                ]
            }
        },
        "presets": [
            "es2015"
        ],
        "plugins": [
            "transform-runtime",
            "syntax-async-functions",
            [
                "transform-async-to-module-method",
                {
                    "module": "bluebird",
                    "method": "coroutine"
                }
            ]
        ]
    },
    "nyc": {
        "reporter": [
            "lcov",
            "text-summary",
            "html"
        ],
        "sourceMap": false,
        "instrument": false,
        "cache": true
    },
    "dependencies": {
        "aws-sdk": "^2.9.0",
        "babel-register": "^6.16.3",
        "bluebird": "^3.4.6",
        "colors": "^1.1.2",
        "commander": "^2.9.0",
        "debug": "^2.3.3",
        "electron-forge-template-angular2": "^1.0.3",
        "electron-forge-template-react": "^1.0.2",
        "electron-forge-template-react-typescript": "^1.0.3",
        "electron-forge-template-vue": "^1.0.2",
        "electron-installer-dmg": "^0.2.0",
        "electron-packager": "^8.5.2",
        "electron-rebuild": "^1.5.7",
        "electron-sudo": "malept/electron-sudo#fix-linux-sudo-detection",
        "electron-windows-store": "^0.10.1",
        "electron-winstaller": "^2.5.0",
        "fs-promise": "^2.0.0",
        "github": "^9.0.0",
        "glob": "^7.1.1",
        "inquirer": "^3.0.1 ",
        "lodash.template": "^4.4.0",
        "log-symbols": "^1.0.2",
        "node-fetch": "^1.6.3",
        "node-gyp": "^3.4.0",
        "nugget": "^2.0.1",
        "opn": "^4.0.2",
        "ora": "^1.1.0",
        "pify": "^2.3.0",
        "resolve-package": "^1.0.1",
        "s3": "^4.4.0",
        "semver": "^5.3.0",
        "spawn-rx": "^2.0.7",
        "sudo-prompt": "^7.0.0",
        "tabtab": "^2.2.1",
        "username": "^2.2.2",
        "yarn-or-npm": "^2.0.2",
        "zip-folder": "^1.0.0"
    },
    "config": {
        "commitizen": {
            "path": "./node_modules/cz-customizable"
        },
        "cz-customizable": {
            "config": "./.cz.js"
        }
    },
    "optionalDependencies": {
        "electron-installer-debian": "^0.5.0",
        "electron-installer-flatpak": "^0.4.0",
        "electron-installer-redhat": "^0.4.0"
    },
    "engines": {
        "node": ">= 6.0"
    }
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
