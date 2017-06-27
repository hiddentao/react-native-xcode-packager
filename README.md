This provides a custom version of `react-native-xcode.sh` which ensures that the bundle always gets built.

The [default XCode packager script](https://github.com/facebook/react-native/blob/master/scripts/react-native-xcode.sh) skips bundle building when building a `Debug` configuration for a simulator target. This is good for normal builds, but when we wish to run automated integration tests (e.g. using Appium) it is essential that we are able to build the `Debug` configuration with bundled JS in order for upload to cloud-based testing solutions.

## How to use

_Note: This assumes you have setup your React Native app manually, i.e. the iOS app is within the ios/
folder and that React Native is in the `node_modules/react-native` folder._

First, install the module:

```shell
$ npm i --save react-native-xcode-packager
```

In XCode, look at the _Bundle React Native code and images_ build phase. It should contain:

```
export NODE_BINARY=node
../node_modules/react-native/packager/react-native-xcode.sh
```

Change this to:

```
export NODE_BINARY=node
../node_modules/react-native-xcode-packager/packager/react-native-xcode.sh
```

## License

Copyright (c) 2017 Ramesh Nair

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
