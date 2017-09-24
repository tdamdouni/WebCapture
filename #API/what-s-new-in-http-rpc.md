# What's New in HTTP-RPC?

_Captured: 2017-09-21 at 13:44 from [dzone.com](https://dzone.com/articles/http-rpc-42-released?edition=325527&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-09-21)_

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

HTTP-RPC 4.2 is now available for [download](https://github.com/gk-brown/HTTP-RPC/releases), as well as via [Cocoapods](https://cocoapods.org/pods/HTTPRPC) for iOS and Maven for Java:

This release includes the following updates:

  * _Refine invocation methods for Swift._ Invocation methods are now parameterized, so it is no longer necessary to cast the return value to the desired type: 
    
        open func invoke<T>(_ method: String, path: String, 
    
            resultHandler: @escaping (T?, Error?) -> Void) -> URLSessionTask? { ... }
    
        open func invoke<T>(_ method: String, path: String, arguments: [String: Any], 
    
            resultHandler: @escaping (T?, Error?) -> Void) -> URLSessionTask? { ... }

  
For example: 
  * _Add support for custom response handlers._ Callers can now perform custom deserialization via a response handler callback. In Swift, the callback is a closure: 
    
        open func invoke<T>(_ method: String, path: String, arguments: [String: Any],
    
            responseHandler: @escaping (Data, String) throws -> T?,
    
            resultHandler: @escaping (T?, Error?) -> Void) -> URLSessionTask? { ... }

For example (using `JSONDecoder` to return a strongly typed result): In Java, the callback is defined as follows: For example (using [Jackson](https://github.com/FasterXML/jackson) to return a strongly typed result): 

For more information, see the project [README](https://github.com/gk-brown/HTTP-RPC/blob/master/README.md).

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
