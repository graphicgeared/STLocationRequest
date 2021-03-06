# STLocationRequest

[![Swift 4.0](https://img.shields.io/badge/Swift-4.0-orange.svg?style=flat)](https://developer.apple.com/swift/)
[![Version](https://img.shields.io/cocoapods/v/STLocationRequest.svg?style=flat)](http://cocoapods.org/pods/STLocationRequest)
[![Downloads](https://img.shields.io/cocoapods/dt/STLocationRequest.svg?style=flat)](http://cocoapods.org/pods/STLocationRequest)
[![License](https://img.shields.io/cocoapods/l/STLocationRequest.svg?style=flat)](http://cocoapods.org/pods/STLocationRequest)
[![Platform](https://img.shields.io/cocoapods/p/STLocationRequest.svg?style=flat)](http://cocoapods.org/pods/STLocationRequest)
[![Contact](https://img.shields.io/badge/contact-@SvenTiigi-blue.svg?style=flat)](https://twitter.com/SvenTiigi/)

STLocationRequest is a simple and elegant way to request the users location services at the very first time written in Swift. The `STLocationRequestController` shows a beautiful 3D 360° Flyover MapView with over 25 cities and landmarks.

<p align="center">
<img src="https://raw.githubusercontent.com/SvenTiigi/STLocationRequest/master/.assets/STLocationRequest.gif" alt="STLocationRequest" width="80%"/>
</p>

## Installation

STLocationRequest is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'STLocationRequest'
```

## Usage

```swift
import STLocationRequest

class ViewController: UIViewController, STLocationRequestControllerDelegate {

    func presentLocationRequestController(){
        let locationRequestController = STLocationRequestController()
        locationRequestController.titleText = "We need your location for some awesome features"
        locationRequestController.allowButtonTitle = "Alright"
        locationRequestController.notNowButtonTitle = "Not now"
        locationRequestController.authorizeType = .requestWhenInUseAuthorization
        locationRequestController.delegate = self
        locationRequestController.present(onViewController: self)
    }
    
}

```
> Please keep in mind that the 3D SatelliteFlyover only works on a real iOS Device ([Read more](#ios-simulator)).

## Customizing
The following properties allow you to customize the behaviour and appearance of the `STLocationRequestController`.

#### mapViewAlpha
```swift
locationRequestController.mapViewAlpha = 0.7
```
> The alpha value for the MapView. Default value is 1.0

#### backgroundColor
```swift
locationRequestController.backgroundColor = .orange
```
> The backgroundcolor for the view of the STLocationRequestController. Default value is white

To perfectly match the design of the `STLocationRequestController` to your iOS app, simply playaround with the parameters `mapViewAlpha` and `backgroundColor` to get your very own design.

<p align="center">
<img width=200 src="https://raw.githubusercontent.com/SvenTiigi/STLocationRequest/master/.assets/STLocationRequest_Purple.jpg" alt="STLocationRequest" title="STLocationRequest">
<img width=200 src="https://raw.githubusercontent.com/SvenTiigi/STLocationRequest/master/.assets/STLocationRequest_Green.jpg" alt="STLocationRequest" title="STLocationRequest">
<img width=200 src="https://raw.githubusercontent.com/SvenTiigi/STLocationRequest/master/.assets/STLocationRequest_Orange.jpg" alt="STLocationRequest" title="STLocationRequest">
<img width=200 src="https://raw.githubusercontent.com/SvenTiigi/STLocationRequest/master/.assets/STLocationRequest_Red.jpg" alt="STLocationRequest" title="STLocationRequest">
</p>

#### titleText
```swift
locationRequestController.titleText = "We need your location for some extraordinary features"
```
> The title which will be presented at the top of the STLocationRequestController. Default-Value: "We need your location for some awesome features"

#### titleFont
```swift
locationRequestController.titleFont = .systemFont(ofSize: 25.0)
```
> The title font. Default-Value: UIFont.systemFontOfSize(25.0)

#### allowButtonTitle
```swift
locationRequestController.allowButtonTitle = "Yes of course"
```
> The title for the allowButton which will trigger the requestWhenInUseAuthorization() or requestAlwaysAuthorization() Method on CLLocationManager. Default value is "Alright"

#### allowButtonFont
```swift
locationRequestController.allowButtonFont = .systemFont(ofSize: 21.0)
```
> The allow button font. Default-Value: UIFont.systemFontOfSize(21.0)

#### notNowButtonTitle
```swift
locationRequestController.notNowButtonTitle = "Nope"
```
> The title for the notNowButton which will dismiss the STLocationRequestController. Default value is "Not now"

#### notNowButtonFont
```swift
locationRequestController.notNowButtonFont = .systemFont(ofSize: 21.0)
```
> The not now button font. Default-Value: UIFont.systemFontOfSize(21.0)

#### mapViewCameraAltitude
```swift
locationRequestController.mapViewCameraAltitude = 600
```
> The altitude for the mapview camera. Default-Value: 600

#### mapViewCameraPitch
```swift
locationRequestController.mapViewCameraPitch = 45
```
> The pitch for the mapview camera. Default-Value: 45

#### mapViewCameraHeadingStep
```swift
locationRequestController.mapViewCameraHeadingStep = 20
```
> The heading step for the mapview camera. Default-Value: 20

#### mapViewCameraRotatinAnimationDuration
```swift
locationRequestController.mapViewCameraRotationAnimationDuration = 4
```
> The mapview camera rotation animation duration. Default-Value: 4

#### authorizeType
```swift
locationRequestController.authorizeType = .requestWhenInUseAuthorization
```
> Set the location request authorize Type for STLocationRequestController. Choose between: .requestWhenInUseAuthorization and .requestAlwaysAuthorization. Default value is .requestWhenInUseAuthorization

#### isPulseEffectEnabled
```swift
locationRequestController.isPulseEffectEnabled = true
```
> Defines if the pulse Effect which will displayed under the location symbol should be enabled or disabled. Default Value: true

#### pulseEffectColor
```swift
locationRequestController.pulseEffectColor = .white
```
> The color for the pulse effect behind the location symbol. Default value: white

#### pulseEffectRadius
```swift
locationRequestController.pulseEffectRadius = 180
```
> The radius of the pulse effect. Default value: 180

#### locationSymbolIcon
```swift
locationRequestController.locationSymbolIcon = .FALocationArrow
```
> Set the location symbol icon which will be displayed in the middle of the STLocationRequest-Controller. The default value is FALocationArrow. You can browse at http://fontawesome.io/icons/ or https://github.com/Vaberer/Font-Awesome-Swift for other icons but be aware to use a icon which is in the context of a location request.

#### locationSymbolSize
```swift
locationRequestController.locationSymbolSize = 150
```
> The size of the location symbol which will be presented in the middle of the location request screen. Default value: 150

#### locationSymbolColor
```swift
locationRequestController.locationSymbolColor = .white
```
> The color of the location symbol which will be presented in the middle of the location request screen. Default value: white

#### isLocationSymbolHidden
```swift
locationRequestController.isLocationSymbolHidden = false
```
> Defines if the location symbol which will be presented in the middle of the location request screen is hidden. Default value: false

#### timeTillPlaceSwitchesInSeconds
```swift
locationRequestController.timeTillPlaceSwitchesInSeconds = 15.0
```
> Set the in the interval for switching the shown places in seconds. Default value is 15 seconds

#### placesFilter
```swift
// Only San Francisco Golden Gate Bridge and the Colosseum in Rome will be shown
locationRequestController.placesFilter = [.sanFranciscoGoldenGateBridge, .romeColosseum]
```
> Fill the optional value placesFilter if you wish to specify which places should be shown. Default value is "nil" which means all places will be shown

## Delegate

You can apply to the `STLocationRequestControllerDelegate` to get notified if the user has authorized or denied the location services, tapped the _Not-Now_ Button or if the `STLocationRequestController` did presented or did disappear.

```swift

func locationRequestControllerDidChange(event: STLocationRequestControllerEvent) {
    switch event {
        case .locationRequestAuthorized:
            break
        case .locationRequestDenied:
            break
        case .notNowButtonTapped:
            break
        case .didPresented:
            break
        case .didDisappear:
            break
    }
}

```

Or you can use the `onChange` closure property to get notified if an `STLocationRequestControllerEvent` occured.

```swift
locationRequestController.onChange = { (event: STLocationRequestControllerEvent) in
    // Evaluate event
}
```

## Custom 3D Flyover Places
An example of adding a custom 3D flyover place to the `STLocationRequestController`.

```swift
// Add a place via latitude and longitude
locationRequestController.addPlace(latitude: 51.960665, longitude: 7.626135)

// Or add a place via CLLocationCoordinate2D
let myCoordinate = CLLocationCoordinate2DMake(51.960665, 7.626135)
locationRequestController.addPlace(coordinate: myCoordinate)
```
> Please keep in mind to verify that your custom location is available in 3D flyover mode. To verify you can check your place on the Apple Maps App by tapping on the 3D-Button.

If you wish to show only your custom 3D flyover places you can simply set the `placesFilter`.

```swift
// Only your custom places will be shown
locationRequestController.placesFilter = [.customPlaces]
```

## Info.plist

Also don't forget to add the usage description key to your `Info.plist` for you selected authorization type.

STLocationRequestControllerAuthorizeType.**requestWhenInUseAuthorization**
```swift
<key>NSLocationWhenInUseUsageDescription</key>
<string>PUT IN YOUR LOCATION EXPLANATION TEXT</string>
```

STLocationRequestControllerAuthorizeType.**requestAlwaysAuthorization**
```swift
<key>NSLocationAlwaysUsageDescription</key>
<string>PUT IN YOUR LOCATION EXPLANATION TEXT</string>
```

This text will be shown in the default iOS location request dialog, which will show up when the user tapped the allow button.

<p align="center">
<img src="https://raw.githubusercontent.com/SvenTiigi/STLocationRequest/master/.assets/iOSLocationRequestDialog.png" alt="iOSRequestDialog" title="iOSRequestDialog" width=300>

</p>

## Presenting-Recommendation

The recommended way to present `STLocationRequestController` is the following way, which is also been implemented in the example application.

```swift
func checkLocationServicePermission() {
    if CLLocationManager.locationServicesEnabled() {
        if CLLocationManager.authorizationStatus() == .denied {
            // Location Services are denied
        } else {
            if CLLocationManager.authorizationStatus() == .notDetermined{
                // Present the STLocationRequestController
                self.presentLocationRequestController()
            } else {
                // The user has already allowed your app to use location services. Start updating location
            }
        }
    } else {
        // Location Services are disabled
    }
}
```
Or you use the convience static function on `STLocationRequestController` which evaluates if an presenting should be performed.

```swift
if STLocationRequestController.shouldPresentLocationRequestController() {
    // Location Services are enabled and authorizationStatus is notDetermined
    // Ready to present STLocationRequestController
    self.presentLocationRequestController()
}
```

## iOS Simulator

Please mind that the 3D Flyover-View will only work on a real iOS device with at least iOS 9.0 installed ([Apple Developer API Reference](https://developer.apple.com/reference/mapkit/mkmaptype/1452553-satelliteflyover)). A Screenshot taken from an **iOS Simulator** running a `STLocationRequestController` visualizes the iOS Simulator behaviour.

<p align="center">
<img src="https://raw.githubusercontent.com/SvenTiigi/STLocationRequest/master/.assets/iOSSimulatorBehavior.jpg" alt="iOSSimulatorBehavior" title="iOSSimulatorBehavior" width=300>

</p>

## Objective-C

An example usage of `STLocationRequestController` in an `Objective-C` project.

```objective-c
#import "ViewController.h"
@import STLocationRequest;

@interface ViewController () <STLocationRequestControllerDelegate>
@end

@implementation ViewController

-(void)presentLocationRequestController{
    STLocationRequestController *locationRequestController = [STLocationRequestController new];
    locationRequestController.titleText = @"We need your location for some awesome features";
    locationRequestController.allowButtonTitle = @"Alright";
    locationRequestController.notNowButtonTitle = @"Not now";
    locationRequestController.mapViewAlpha = 0.9;
    locationRequestController.backgroundColor = [UIColor lightGrayColor];
    locationRequestController.authorizeType = STLocationRequestControllerAuthorizeTypeRequestWhenInUseAuthorization;
    locationRequestController.delegate = self;
    [locationRequestController presentOnViewController:self];
}

-(void)locationRequestControllerDidChange:(enum STLocationRequestControllerEvent)event{
    switch (event) {
        case STLocationRequestControllerEventlocationRequestAuthorized:
            break;
        case STLocationRequestControllerEventlocationRequestDenied:
            break;
        case STLocationRequestControllerEventnotNowButtonTapped:
            break;
        case STLocationRequestControllerEventdidPresented:
            break;
        case STLocationRequestControllerEventdidDisappear:
            break;
    }
}

```
## Credits
`STLocationRequest` is using following libraries.

+ [Font-Awesome-Swift](https://github.com/Vaberer/Font-Awesome-Swift)
+ [SwiftPulse](https://github.com/ctews/SwiftPulse)

## License

```
STLocationRequest
Copyright (c) 2015 Sven Tiigi <sven@tiigi.de>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
