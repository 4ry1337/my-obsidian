# Tints  
**Here beauty master and clients meet in one click**

# Development

Flutter ver - 3.7.12,  
Dart ver - 2.19.6

## State management  
State management implemented with GetX and bloc  
- [Getx](https://pub.dev/packages/get) is used for general app routing and widgets' logic  
- [BloC](https://pub.dev/packages/flutter_bloc) used in screen logic

## Folder Structure
using public api example:
```Dart
import "package:tints/shared/index.dart";
import "package:tints/repositories/repositories.dart";
import "package:tints/controllers/controllers.dart";

///inside files, e.g ./shared/index.dart///
export 'enums/enums.dart';
export 'theme/theme.dart';
export 'utils/utils.dart';
export 'widgets/widgets.dart';
```

project
- controllers
	- controllers.dart // has all exports
- models
- repositories
	- SgAppData - shared prefs
- screens
- shared
	- widgets
	- theme
	- utils
	- widgets
		- buttons
		- calendar
		- cards
		- inputs
		- dialogs
		- chips
		- sheets