# React-native

## Infrastructure

There is no need to install **Xcode command-line tools** if Xcode is installed. It is part of it. See [Building from the Command Line with Xcode FAQ] for more information about command-line tools.

[Expo] seems to be to react-native as create-react-app to react.

[CocoaPods] is a dependency manager for Swift and Objective-C Cocoa projects.

[Metro] is to react-native as webpack to react.

[Building from the Command Line with Xcode FAQ]: https://developer.apple.com/library/archive/technotes/tn2339/_index.html
[Expo]: https://expo.io
[CocoaPods]: https://cocoapods.org
[Metro]: https://facebook.github.io/metro/

## Expo

`⌘D` in Expo app: open debug panel

## Xcode

```
xed ios  # open ios folder within project root in Xcode
```

## Gradle

```
./gradlew tasks.   # list available tasks
./gradlew -m task  # dry run to see all subtasks
./gradlew clean.   # delete build dir
```

## Android emulator and ADB

```
emulator -list-avds   # list existing android virtual devices
emulator -avd <name>  # launch emulator with virtual device
adb devices           # list all connected devices
adb install foo.apk   # install apk
```

## iOS simulator

```
xcrun simctl list devices              # list available devices
npm run ios -- --simulator "iPhone 11 Pro" # pick device
```

## Styling

**The most frequently used approach** is using React Native Stylesheet objects. They defined in the same file under the component or in a separate file `styles.js` next to it.

A good tip was passing `styles` prop to own components and enabling the parent to overload any style with that:

```
const RegularText = ({ children, style, ...props }) => (
  <Text {...props} style={{ fontSize: 20, ...style }}>
    {children}
  </Text>
)
```

**The second frequently used approach** are Styled Components [which support React Native too](https://styled-components.com/docs/basics#react-native). Suggested for example [here](https://blog.echobind.com/a-comparison-of-three-methods-for-styling-components-in-react-native-88ece2fdcdea).

### Global styles

There is [limited styling inheritance](https://reactnative.dev/docs/text#limited-style-inheritance) in React Native because of component encapsulation. They propose creating own components that are reused across the system similarly how React docs suggest.

Vast majority of developers do not follow the rule though. Often they create a theme file that exports either [variables for certain style properties](https://www.reactnative.guide/8-styling/8.1-theme-variables.html) or more often whole stylesheet objects.

The best tips for such approach are summed up here: [React Native Styling: Structure for Style Organization](https://thoughtbot.com/blog/structure-for-styling-in-react-native)

## App structure

Good general suggestions about the structure in [thoughtbot article](https://thoughtbot.com/blog/best-practices-while-developing-a-react-native-app).

In general apps can be structured by features/routes or file types as suggested in [React FAQ](https://reactjs.org/docs/faq-structure.html).

Other general tips (not only) how to structure React Native app: [An efficient way to structure React Native projects](https://cheesecakelabs.com/blog/efficient-way-structure-react-native-projects/)

### Rather flat

```
/api
	- (separated services)
/assets
	- (fonts, images)
/styles
	- colors
	- index
	- typography
/navigation
/screens
	- (no stylesheets)
/ducks
/components
	- (components resable across whole project)
	- (dummy components only)
/containers
/locales
```

### Feature-based aka. Modules

Composite structure with some good ideas and arguments: [How to better organize your React applications?](https://medium.com/@alexmngn/how-to-better-organize-your-react-applications-2fd3ea1920f1)


```
/api
/components         # components used across multiple modules
	/buttons          # single nesting if convenient
		Button.tsx
		IconButton.tsx
		Callout.tsx
	Card.tsx
/locales            # locales to use across multiple modules
	en.json
/locations...       # isolated module contained by navigator
/login...           # isolated module contained by navigator
/navigation         # top navigator
	AppDrawerNavigator.tsx
	types.ts          # all navigation types (circ dep otherwise)
/search             # isolated module contained by navigator
	/BookingConfirmationScreen # module screens
	/CapacitySelectionScreen
	/components                # components used across module
		BookNowButton.tsx
		RoomCapacity.tsx
	/containers                # containers used across module
		PeopleLookingAtThis.tsx
	/DateSelectionScreen
	/ducks                     # redux actions/reducers/selectors
	/locales
		en.json                  # module-level locales
	/SearchResultDetailScreen
	/SearchResultsScreen
		/components              # nested components for this screen
			EditFiltersButton.tsx
		/containers              # nested containers for this screen
			ResultListContainer.tsx
			FilterListContainer.tsx
		index.tsx                # barrel file for easy import
		SearchResultsScreen.tsx  # screen component
	/services
	/TypeSelectionScreen
	SearchStackNavigator.tsx   # module navigator
/styles
	colors.ts
	typography.ts
```

Originally more explicit structure and naming of modules was considered:

```
...
/modules
	/locations...
	/login...
	/search
		/containers
			PeopleLookingAtThis.tsx
		/components
			BookNowButton.tsx
			RoomCapacity.tsx
		/ducks
		/locales
			en.json
		/screens
			/BookingConfirmationScreen
			/CapacitySelectionScreen
			/DateSelectionScreen
			/SearchResultDetailScreen
			/SearchResultsScreen
				/components
					EditFiltersButton.tsx
				/containers
					ResultListContainer.tsx
					FilterListContainer.tsx
				index.tsx
				SearchResultsScreen.tsx
			/TypeSelectionScreen
		/services
		SearchStackNavigator.tsx
...
```

But that cause 6 levels of nesting:

```
/modules/search/screens/SearchResultsScreen/containers/ResultList.tsx file:
import { Button } from '../../../../../components/Button'
```

Now only 4 as suggested by React Native docs.

```
/search/SearchResultsScreen/containers/ResultsList.jsx file
Import { Button } from '../../../components/Button'
```


## React navigation

When using nested navigators, their navigation is independent. For example if `DrawerNavigator` is parent of `StackNavigator`, `navigate.jumpTo` on `DrawerNavigator` does not change active screen of `StackNavigator` when returning back to it.

When it is desired to activate a specific nested screen, `screen` parameter [has to be provided](https://reactnavigation.org/docs/nesting-navigators/#navigating-to-a-screen-in-a-nested-navigator).


## Component libraries

[Comparison of react-native component libraries][1] shows most popular UI kits. [react-native-elements][2] is the most popular one, winning also in [React Native Directory][3]. [react-native-paper][5] is the most popular Material Design based library.

[react-native-vector-icons][4] is the most popular icon library with *recommended* tag in React Native Directory.

[1]: https://www.npmtrends.com/react-native-elements-vs-native-base-vs-react-native-material-ui-vs-react-native-paper-vs-react-native-material-kit-vs-teaset-vs-react-native-ui-lib
[2]: https://reactnativeelements.com
[3]: https://reactnative.directory/?order=stars
[4]: https://oblador.github.io/react-native-vector-icons/
[5]: https://reactnativepaper.com