# AuthClient-Demo

This is a demo for constructing a basic authentication layer for iOS development. Based on the iOS design patterns video from www.raywenderlich.com.

## Models

### AuthToken

An `AuthToken` contains the information that a `HTTPURLRequest` should obtain for privileged access to endpoints.

```
protocol AuthToken {
  var authHeaders: [String: String] { get }
}

extension AuthToken {
  func setAuthHeaders(on request: inout URLRequest) {
    authHeaders.forEach {
      request.setValue($0.value, forHTTPHeaderField: $0.key)
    }
  }
}
```
