# Flutter_doc_CokBK_IMG_Fade_images_with_placeholder
 https://docs.flutter.dev/cookbook/images/fading-in-images#complete-example-1
Fade in images with a placeholder
=================================

1.  [Cookbook](https://docs.flutter.dev/cookbook)
2.  [Images](https://docs.flutter.dev/cookbook/images)
3.  [Fade in images with a placeholder](https://docs.flutter.dev/cookbook/images/fading-in-images)

When displaying images using the default `Image` widget, you might notice they simply pop onto the screen as they're loaded. This might feel visually jarring to your users.

Instead, wouldn't it be nice to display a placeholder at first, and images would fade in as they're loaded? Use the [`FadeInImage`](https://api.flutter.dev/flutter/widgets/FadeInImage-class.html) widget for exactly this purpose.

`FadeInImage` works with images of any type: in-memory, local assets, or images from the internet.

[](https://docs.flutter.dev/cookbook/images/fading-in-images#in-memory)In-Memory
--------------------------------------------------------------------------------

In this example, use the [`transparent_image`](https://pub.dev/packages/transparent_image) package for a simple transparent placeholder.

content_copy

```
FadeInImage.memoryNetwork(
  placeholder: kTransparentImage,
  image: 'https://picsum.photos/250?image=9',
),
```

### [](https://docs.flutter.dev/cookbook/images/fading-in-images#complete-example)Complete example

content_copy

```
import 'package:flutter/material.dart';
import 'package:transparent_image/transparent_image.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    const title = 'Fade in images';

    return MaterialApp(
      title: title,
      home: Scaffold(
        appBar: AppBar(
          title: const Text(title),
        ),
        body: Stack(
          children: <Widget>[
            const Center(child: CircularProgressIndicator()),
            Center(
              child: FadeInImage.memoryNetwork(
                placeholder: kTransparentImage,
                image: 'https://picsum.photos/250?image=9',
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

![Fading In Image Demo](https://docs.flutter.dev/assets/images/docs/cookbook/fading-in-images.gif)

[](https://docs.flutter.dev/cookbook/images/fading-in-images#from-asset-bundle)From asset bundle
------------------------------------------------------------------------------------------------

You can also consider using local assets for placeholders. First, add the asset to the project's `pubspec.yaml` file (for more details, see [Adding assets and images](https://docs.flutter.dev/ui/assets/assets-and-images)):

content_copy

```
 flutter:
   assets:
+    - assets/loading.gif

```

Then, use the [`FadeInImage.assetNetwork()`](https://api.flutter.dev/flutter/widgets/FadeInImage/FadeInImage.assetNetwork.html) constructor:

content_copy

```
FadeInImage.assetNetwork(
  placeholder: 'assets/loading.gif',
  image: 'https://picsum.photos/250?image=9',
),
```

### [](https://docs.flutter.dev/cookbook/images/fading-in-images#complete-example-1)Complete example

content_copy

```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    const title = 'Fade in images';

    return MaterialApp(
      title: title,
      home: Scaffold(
        appBar: AppBar(
          title: const Text(title),
        ),
        body: Center(
          child: FadeInImage.assetNetwork(
            placeholder: 'assets/loading.gif',
            image: 'https://picsum.photos/250?image=9',
          ),
        ),
      ),
    );
  }
}
```
