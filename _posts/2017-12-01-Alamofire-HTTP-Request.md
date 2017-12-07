---
layout: post 

title: Alamofire HTTP Request 

date: 2017-12-01 22:57:39 

author: C.W.Kim 

categories: Iron

tags: Alamofire post 
---
### Alamofire HTTP Request ### 
> Alamofire HTTP Post -> REST -> Node.JS
```
let parameters: Parameters = [
    "foo": "bar",
    "baz": ["a", 1],
    "qux": [
        "x": 1,
        "y": 2,
        "z": 3
    ]
]

// All three of these calls are equivalent
Alamofire.request("https://httpbin.org/post", method: .post, parameters: parameters)
Alamofire.request("https://httpbin.org/post", method: .post, parameters: parameters, encoding: URLEncoding.default)
Alamofire.request("https://httpbin.org/post", method: .post, parameters: parameters, encoding: URLEncoding.httpBody)

// HTTP body: foo=bar&baz[]=a&baz[]=1&qux[x]=1&qux[y]=2&qux[z]=3
```

##### POST Request with JSON-Encoded Parameters

```
let parameters: Parameters = [
    "foo": [1,2,3],
    "bar": [
        "baz": "qux"
    ]
]

// Both calls are equivalent
Alamofire.request("https://httpbin.org/post", method: .post, parameters: parameters, encoding: JSONEncoding.default)
Alamofire.request("https://httpbin.org/post", method: .post, parameters: parameters, encoding: JSONEncoding(options: []))

// HTTP body: {"foo": [1, 2, 3], "bar": {"baz": "qux"}}

```


```swift
func request(url:String, method: String, params: [String: String], completion: ([AnyObject])->() ){
    if let nsURL = NSURL(string:url) {
        let request = NSMutableURLRequest(URL: nsURL)
        if method == "POST" {
            // convert key, value pairs into param string
            postString = params.map { "\($0.0)=\($0.1)" }.joinWithSeparator("&")
            request.HTTPMethod = "POST"
            request.HTTPBody = postString.dataUsingEncoding(NSUTF8StringEncoding)            
        }
        else if method == "GET" {
            postString = params.map { "\($0.0)=\($0.1)" }.joinWithSeparator("&")
            request.HTTPMethod = "GET"
        }
        else if method == "PUT" {
            putString = params.map { "\($0.0)=\($0.1)" }.joinWithSeparator("&")
            request.HTTPMethod = "PUT"
            request.HTTPBody = putString.dataUsingEncoding(NSUTF8StringEncoding)                        
        }
        // Add other verbs here

        let task = NSURLSession.sharedSession().dataTaskWithRequest(request) {
            (data, response, error) in
            do {

                // what happens if error is not nil? 
                // That means something went wrong.

                // Make sure there really is some data
                if let data = data {
                    let response = try NSJSONSerialization.JSONObjectWithData(data, options:  NSJSONReadingOptions.MutableContainers) 
                    completion(response)                    
                }
                else {
                    // Data is nil.
                }
            } catch let error as NSError {
                print("json error: \(error.localizedDescription)")
            }
        }
        task.resume()            
    }
    else{
        // Could not make url. Is the url bad?
        // You could call the completion handler (callback) here with some value indicating an error
    }    
}
```



