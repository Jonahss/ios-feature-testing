# Features

## Essential
 
| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	|
|---------	|-------	|--------------	|------------	|-----	|
| iOS 8+ support          	| 💚 	| 💚 	| 💚 	| 💚 	|
| Run from CI             	| 💚 	| 💚 	| 💚 	| 💚 	|
| Animation waiting       	| 💛[¹](#footnotes)	|    	| 💚  	| 💚  	|

## UIKit Interactions

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	|
|---------	|-------	|--------------	|------------	|-----	|
| Reading UILabels         	| 💚	| 💚  	| 💚 	| 💚 	|
| UITableView interaction   	| 💚   	| 💚 	| ❌ 	| 💚 	|
| Scrolling UIScrollViews  	| 💚   	| 💚 	| 💚 	| 💚 	|
| Standard UIAlertViews     	| 💚   	| 💚 	| ❌ 	| 💚 	| 
| Typing into UITextFields   	| 💛[²](#footnotes) 	| 💚  	| 💚	| 💚	|
| Tapping UIControls        	| 💚  	| 💚	| 💚	| 💚	|
| Sliding UISliders         	| 💚 	| ❌	| 💛[³](#footnotes)	| 💚 	|
| UIKit visibility          	| 💚 	| 💚	| 💚	| 💚	|
| UIActionSheet interaction 	| 💚 	| 💚 	| 💚 	| 💚 	|
| UIPickerView interaction  	| 💚 	| 💛[⁴](#footnotes)	| 💚 	| 💚 	|
| Swipe to delete           	| ❌ 	| ❌ 	| ❌ 	| 💚 	|

## Hybrid Apps

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	|
|---------	|-------	|--------------	|------------	|-----	|
| UIWebView interaction   	| ❌ 	| 💚 	| 💚 	| 💚 	|
| WKWebView interaction   	| ❌ 	| 💚 	| ❌[⁵](#footnotes) 	| ❌ 	|

## External to App

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	|
|---------	|-------	|--------------	|------------	|-----	|
| Remote controllers          	| ❌ 	| 💚 	| ❌[⁵](#footnotes)	| ❌ 	|
| System UIAlertViews        	| ❌ 	| 💚 	| 💚	| ❌ 	|
| Backgrounding/foregrounding 	| ❌ 	| ❌ 	| ❌	| ❌ 	|


## Developer Niceties

| Feature 	| Frank 	| UIAutomation 	| Subliminal 	| KIF 	|
|---------	|-------	|--------------	|------------	|-----	|
| Objective-C                                 	| ❌ 	| ❌ 	| 💚 	| 💚 	|
| BDD-style                                   	| 💚 	| ❌  	| ❌ 	| ❌ 	|
| Can be debugged                            	| 💚 	| ❌  	| 💛[⁶](#footnotes)	| 💚 	|
| Does not require Instruments.app            	| 💚 	| ❌  	| ❌ 	| 💚 	|
| Focus tests                                 	| 💚 	| ❌    	| 💚 	| 💚[⁷](#footnotes) 	|
| Cocoapods support                           	| 💚 	| n/a 	| 💚 	| 💚 	|
| Inspect view hierarchy from framework’s PoV 	| 💚 	| 💚  	| 💚 	| 💛[⁸](#footnotes) 	|

💚 = Full support
💛 = Support with caveats

### Versions

* Xcode 6.1
* iOS 8.1
* Frank 1.2.3
* Subliminal 1.1.0 - [shared/Xcode6 branch - d99fef4 commit](https://github.com/inkling/Subliminal/commit/d99fef42529589373adc1948aede98aed0fbe9de)
* KIF - 3.0.8

### Footnotes

* ¹ Some animations are handled without interaction, while others require manual waiting.
* ² Sometimes Frank is so eager to type, he doesn’t wait for the UITextField to fully focus, leading to dropped characters. Workarounds are possible.
* ³ Subliminal can slide a slider and successfully call delegate methods, but the computation of the physical nub offsets are left to you.
* ⁴ UIAutomation makes each UIPicker selection on value at a time, making selection very slow. Also, if the date is not selectable UIAutomation will silently fail.\
* ⁵ Subliminal cannot interact with these elements directly, but can call into UIAutomation’s JavaScripts via `SLTerminal -eval:`.
* ⁶ Subliminal loops over Objective-C code which calls JavaScript asynchronously via Instruments making debugging possible, but quite difficult.
* ⁷ Tests can be focused in Xcode via tapping the gutter (ala XCTest) but not via the command line.
* ⁸ You can use the [Accessibility Inspector](https://developer.apple.com/library/ios/technotes/TestingAccessibilityOfiOSApps/TestAccessibilityiniOSSimulatorwithAccessibilityInspector/TestAccessibilityiniOSSimulatorwithAccessibilityInspector.html) to identify elements for KIF to interact with, but there isn’t a direct way to view the hierarchy or identify elements which KIF ignores because they are accessibility containers.
