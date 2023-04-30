# Flutter Web - Download Files from URL

How to implement file download functionality in a Flutter web application using JavaScript.

## Steps

### Step 1: Set up your Flutter project

Create a new Flutter project or open your existing project.

### Step 2: Import the dart:js library in your Dart file

In your Dart file where you want to download the file (e.g., `main.dart`), import the `dart:js` library.

```dart
import 'dart:js' as js;
```

### Step 3: Define the download function

Define a function called downloadFile that will execute JavaScript code to download the file. This function should take the URL of the file as a parameter.

```dart
void downloadFile(String fileUrl) {
  js.context.callMethod('downloadFile', [fileUrl]);
}
```

### Step 4: Create the JavaScript file

Create a JavaScript file named `custom_script.js` and place it in the web folder of your Flutter project.

Write the JavaScript code in `custom_script.js` to download the file using the `a` element and the click event.

```javascript
function downloadFile(fileUrl) {
  var link = document.createElement('a');
  link.href = fileUrl;
  link.download = '';
  link.click();
}
```

### Step 5: Include the JavaScript file

In the web folder of your Flutter project, locate the `index.html` file.

Add a script tag to include the JavaScript file you created (`custom_script.js`) within the `<body>` section of the `index.html` file.

```html

<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flutter Web App</title>
  </head>
  <body>
    <script src="custom_script.js"></script>
    <script src="main.dart.js" type="application/javascript"></script>
  </body>
</html>
```

### Step 6: Trigger file download

In your Flutter widget, add a button (e.g., `ElevatedButton`) where you want to trigger the download of a file.

```dart

ElevatedButton(
  onPressed: () {
    String fileUrl = 'https://example.com/file.pdf'; // Replace with the actual file URL
    downloadFile(fileUrl);
  },
  child: Text('Download File'),
),
```

### Step 7: Build and run the Flutter web app

Build and run your Flutter web app.

When the button is clicked, the JavaScript function `downloadFile` will be called, and the file will start downloading.


##### Found this useful? Follow me on [GitHub](https://github.com/iAhmadAmin) 😇
