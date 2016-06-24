# ISTimeline
ISTimeline is a simple timeline view written in Swift 2.2

![ISTimeline](/screenshots/timeline.png "ISTimeline")

## Requirements
- iOS 8.0 or higher
- Swift 2.2

## CocoaPods
We recommend to use CocoaPods:

```
pod 'ISTimeline', '~> 0.0.1'
```

Or just drop the files ISPoint.swift and ISTimeline.swift into your project.

## Usage

### Import
```swift
import ISTimeline
```

### Integration
We recommend to use the timeline view in your storyboard. Just add a plain view and set the custom class property to `ISTimeline`.

![Custom class](/screenshots/custom_class.png "Custom class")

Or add the view programmatically:

```swift
let frame = CGRectMake(0, 20, 300, 400)

let timeline = ISTimeline(frame: frame)
timeline.backgroundColor = UIColor.whiteColor()

self.view.addSubview(timeline)
```

### ISPoint
Each bubble is represented by an ISPoint object in the points array. ISPoints has several properties:  
`var title:String` shown in the bubble  
`var description:String?` shown below the bubble  
`var pointColor:UIColor` the color of each point in the line  
`var lineColor:UIColor` the color of the line after a point  
`var touchUpInside:Optional<(point:ISPoint) -> Void>` a callback, which is triggered after a touch inside a bubble  
`var fill:Bool` fills the point in the line (default: `false`)

Example point:
```swift
let point = ISPoint(title: "my title")
point.description = "my awesome description"
point.lineColor = UIColor.redColor()
point.fill = true

timeline.points.append(point)
```

#### Initializers
The designated initializer is:
```swift
ISPoint(title:String, description:String, pointColor:UIColor, lineColor:UIColor, touchUpInside:Optional<(point:ISPoint) -> Void>, fill:Bool)
```

You also can use one the convenience initializers:
```swift
ISPoint(title:String, description:String, touchUpInside:Optional<(point:ISPoint) -> Void>)
```
```swift
ISPoint(title:String, touchUpInside:Optional<(point:ISPoint) -> Void>)
```

Or even this one:
```swift
ISPoint(title:String)
```

### Add points to the timeline
To add points to the timeline you can simple create and set your points array to the property `timeline.points` or you can append each point one after the other.
```swift
let myPoints = [
  ISPoint(title: "first"),
  ISPoint(title: "second"),
  ISPoint(title: "third")
]
timeline.points = myPoints
```
Append points:
```swift
timeline.points.append(ISPoint(title: "fourth"))
```

### Colors
You can customize the following timeline colors:  
`var bubbleColor:UIColor` color of every bubble (default `.init(red: 0.75, green: 0.75, blue: 0.75, alpha: 1.0)`)  
`var titleColor:UIColor` color of the title in the bubble (default `.whiteColor()`)  
`var descriptionColor:UIColor` color the description text (default `.grayColor()`)  
Points can be colored as described above.

### Line width and point radius
Some common parameters can be adjusted:  
`var pointDiameter:CGFloat` diameter of a point in the line (default `6.0`)  
`var lineWidth:CGFloat` the thickness of the line (default `2.0`)  
`var bubbleRadius:CGFloat` the radius of the bubble corners (default `2.0`)  

### Intents
You can add some padding by setting the content insets. This currently can only be done programmatically.
```swift
timeline.contentInset = UIEdgeInsetsMake(20.0, 20.0, 20.0, 20.0)
```

### Clip subviews
Per default, the timeline clips all subviews to its bounds. If you would like to change this behavior just set it to `false`.
```swift
timeline.clipsToBounds = false
```

## TODOs
- [ ] show images in the timeline
- [ ] animate the appending and removing of an entry

## License

ISTimeline is licensed under the terms of the Apache License 2.0. See the LICENSE file for more info.

## Contribution

Feel free to fork the project and send us a pull-request! :sunglasses:
