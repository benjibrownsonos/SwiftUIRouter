SwiftUI Router
==============
> Easy and maintainable app navigation with path based routing for SwiftUI.

![SwiftUI](https://img.shields.io/github/v/release/frzi/SwiftUIRouter)
[![SwiftUI](https://img.shields.io/badge/SwiftUI-orange.svg)](https://developer.apple.com/xcode/swiftui)
[![Swift](https://img.shields.io/badge/Swift-5.3-orange.svg)](https://swift.org)
[![Xcode](https://img.shields.io/badge/Xcode-12.4-blue.svg)](https://developer.apple.com/xcode)
[![MIT](https://img.shields.io/badge/license-MIT-black.svg)](https://opensource.org/licenses/MIT)

With **SwiftUI Router** you can power your SwiftUI app with path based routing. By utilizing a path based system, navigation in your app becomes more flexible and easier to maintain.

## Index
* [Installation](#installation-)
* [Documentation](#documentation-)
* [Usage](#usage-)

## Installation 🚀
If your project is a Swift Package itself, add the dependency to the `Package.swift`:
```swift
.package(url: "https://github.com/frzi/SwiftUIRouter.git", from: "0.2.0")
```
Or if you're using Xcode, add the dependency to your project via *File > Swift Packages > Add Package Dependency...* and use the above url.

Once added, import the package in your code:
```swift
import SwiftUIRouter
```

<br>

## Documentation 📚

<br>

## Usage 💪
### `Router`
```swift
Router {
	RootView()
}
```
### `Route`
```swift
Route(path: "news/*") {
	NewsScreen()
}
Route(path: "settings") {
	SettingsScreen()
}
Route(path: "user/:id?") { info in
	UserScreen(id: info.parameters["id"])
}
```
#### Parameters
#### Parameter validation
```swift
func validateUserID(routeInfo: RouteInformation) -> UUID? {
	UUID(routeInfo.parameters["uuid"] ?? "-")
}

Route(path: "user/:uuid", validator: validateUserID) { uuid in
	UserScreen(userID: uuid)
}
```

### `NavLink`
```swift
NavLink(to: "/news/latest") {
	Text("Latest news")
}
```

### `SwitchRoutes`
```swift
SwitchRoutes {
	Route(path: "latest") {
		LatestNewsScreen()
	}
	Route(path: "article/:id") { info in
		NewsArticleScreen(articleID: info.parameters["id"]!)
	}
	Route(path: ":unknown") {
		ErrorScreen()
	}
	Route {
		NewsScreen()
	}
}
```

### `Navigate`
```swift
Navigate(to: "/error-404")
```

### `Navigator`
```swift
@EnvironmentObject var navigator: Navigator
```
