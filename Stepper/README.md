## Stepper

```swift
struct ContentView: View {
    
    @State private var sleepAmount = 8.0
    
    var body: some View {
        Stepper(value: $sleepAmount, in: 4...12, step: 0.25) {
//            Text("\(sleepAmount, specifier: "%.2f") hours")
            Text("\(sleepAmount, specifier: "%g") hours")
        }
    }
}

```

[Back to top](../README.md)