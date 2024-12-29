# Silent Failure of Expo Camera takePictureAsync in Expo

This repository demonstrates a common, yet subtle bug when using the Expo Camera API.  The `takePictureAsync` method might fail silently if called before the camera has finished initializing. This often leads to debugging difficulties because no error is thrown; the promise simply hangs indefinitely.

## How to Reproduce

1. Clone this repository.
2. Install dependencies using `npm install` or `yarn install`.
3. Run the app using `expo start`.
4. Observe that the app crashes silently. The photo will never be taken. 

## Solution

Ensure that `takePictureAsync` is only called after the camera has fully initialized.  This involves using the `onCameraReady` callback or checking the `isCameraReady` property (if available in your Expo version).