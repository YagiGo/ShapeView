# ShapeView [![Build Status](https://travis-ci.org/lm2343635/ShapeView.svg?branch=master)](https://travis-ci.org/lm2343635/ShapeView) [![Version](https://img.shields.io/cocoapods/v/ShapeView.svg?style=flat)](https://cocoapods.org/pods/ShapeView) [![License](https://img.shields.io/cocoapods/l/ShapeView.svg?style=flat)](https://cocoapods.org/pods/ShapeView) [![Platform](https://img.shields.io/cocoapods/p/ShapeView.svg?style=flat)](https://cocoapods.org/pods/ShapeView)

ShapeView support to create a view with the customized shape, shadow and transparent background at the same time.

## Installation

ShapeView is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'ShapeView'
```

ShapeView supports the following attributes.

- ```path: ShapePath?```
- ```shadowRadius: CGFloat```
- ```shadowColor: UIColor```
- ```shadowOpacity: Float```
- ```shaowOffset: CGSize```
- ```blurEffectStyle: UIBlurEffect.Style?```
- ```blurAlpha: CGFloat```

To create a customized shape, use ```.custom``` to draw the shape as the following.

```Swift
view.path = .custom {
    let labelHeight = view.frame.height - Const.height
    let raduis = labelHeight / 2

    $0.move(to: CGPoint(x: raduis, y: 0))
    $0.addArc(withCenter: CGPoint(x: view.frame.width - raduis, y: raduis), radius: raduis, startAngle: -.pi / 2, endAngle: .pi / 2, clockwise: true)
    $0.addLine(to: CGPoint(x: Const.left + Const.height, y: labelHeight))
    $0.addLine(to: CGPoint(x: Const.left + Const.height / 2, y: view.frame.height))
    $0.addLine(to: CGPoint(x: Const.left, y: labelHeight))
    $0.addArc(withCenter: CGPoint(x: raduis, y: raduis), radius: raduis, startAngle: .pi / 2, endAngle: -.pi / 2, clockwise: true)
}
```

In the demo app, a dialog view is created with the code above.

![Demo](https://raw.githubusercontent.com/lm2343635/ShapeView/master/screenshoots/demo.png)

Some shapes are prepared in the ShapeView struct.

```Swift
corner(radius: CGFloat, bounds: @escaping () -> CGRect)
dialog(radius: CGFloat, arrowPosition: DialogArrowPosition, bounds: @escaping () -> CGRect)
```

Here is a demo to create a dialog view.

```Swift
view.path = .dialog(radius: 10, arrowPosition: .right(center: 50, width: 40, height: 20)) {
	return self.bounds
}
```

## Author

lm2343635, lm2343635@126.com

## License

RxOrientation is available under the MIT license. See the LICENSE file for more info.
