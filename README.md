# NWaysClient (Swift package)

The N-Ways Maps Platform API client for iOS 15+ and macOS 12+ (Foundation only): one method per API operation (geocoding, postcodes, places,
routes, the route matrix, fares, static maps, fleet tracking…), your key in the `X-NWays-Api-Key` header, and errors
with the HTTP status, the `reason` and `Retry-After`. Generated from the N-Ways OpenAPI files.

Docs: https://nways.ng/developers/client-libraries · API reference: https://nways.ng/developers/reference

## Install

In Xcode: **File → Add Package Dependencies…** and enter `https://github.com/n-ways/client-swift`; or in `Package.swift`:

```swift
.package(url: "https://github.com/n-ways/client-swift", from: "1.1.0")
```

with the `NWaysClient` product.

## Example

```swift
import NWaysClient

let nways = NWaysClient(apiKey: "YOUR_API_KEY")
do {
    let answer = try await nways.geocode(q: "Allen Avenue, Ikeja", limit: 3)
    print(answer.results.first?.name ?? "nothing found")
} catch let e as NWaysError {
    print(e.status, e.reason ?? "", e.message)
}
```

Keep server keys (restricted to your servers' IP addresses) out of web pages and apps.

## Licence

The client's code is licensed under the [Apache License, Version 2.0](LICENSE) (`Apache-2.0`), Copyright 2026
N-WAYS LIMITED; see [NOTICE](NOTICE).

The licence covers the code, not the data the API returns. N-Ways maps and data are built on OpenStreetMap,
© OpenStreetMap contributors, available under the [Open Database License (ODbL)](https://www.openstreetmap.org/copyright);
credit "N-Ways · © OpenStreetMap contributors" wherever you show them. Using the API needs an N-Ways API key and is
governed by the [N-Ways Maps Platform terms](https://nways.ng/developers/terms).
