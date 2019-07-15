This project contains the source code for the drone user interface. The generated javascript and css assets are embedded into a Go source file which is imported into the main drone application, using go get.

## Building

To compile the source and create minified css and javascript assets:

```text
yarn install    # install project dependencies

yarn run format # formats the codebase
yarn run lint   # lints the codebase
yarn run test   # tests the codebase
yarn run build  # builds the production bundle
```

## Running

To run a devserver with watching, hotreloading and proxy to drone server:

```text
export DRONE_SERVER=<drone server>
export DRONE_TOKEN=<drone api token>

yarn run start
```

For example:

```text
export DRONE_SERVER=http://your.drone.server
export DRONE_TOKEN=eyJhbGciOiJIUzI1NiIsIn...

yarn run start
```

Note you will need to retrieve your drone user token from the tokens screen in the drone user interface. When the server is running you can open the following url in your browser:

```text
http://localhost:9999
```

## Releases

To bundle and embed the code in a Go source file install the following command line utility:

```text
go get github.com/bradrydzewski/togo
```

To generate the Go source file run the following command:

```text
go generate ./...
go install ./...
```

__Note__ that for security reasons we will not accept a pull request that updates embedded Go asset file since we are not able to easily review the embedded, minified code. This file is instead automatically generated by our build server to prevent tampering.
