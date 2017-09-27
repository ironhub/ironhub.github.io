---
layout: post

title: Swift Closure Example

date: 2017-09-26 14:29:11

author: C.W.Kim

categories: Swift

tags: Swift Closure
---

### Swift Closure ###

```swift


class ViewHelper {
    var pviewX = UITableView()
    var viewY = UIView()
    var viewX = UIView()
    
    lazy var getView:
        (UIView) -> (UITableView?) = {
             [unowned self] (aView: UIView ) -> (UITableView?) in
                if let sView = aView.superview {
                    if sView.isKind(of: UITableView.self ) {
                        print("*******")
                        return sView as! UITableView
                    } else {
                        print(".......")
                        return 	self.getView(sView)
                    }
                } else {
            return nil
            }
    }

    func showMe() {
        viewX.addSubview(viewY)
        pviewX.addSubview(viewX)
        
        let myTableView = getView(viewY)
        print("Hello")
        print ( myTableView ?? "xxx" )
    }
    
}

let helper:ViewHelper = ViewHelper()
helper.showMe()




```

