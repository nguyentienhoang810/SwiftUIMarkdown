# SwiftUI memo

## Adding a navigation bar
```swift
struct ContentView: View {
    var body: some View {
        Form{
            Text("hi there")
        }
    }
}
```
![](imgs/nav/no-nav.png)

```swift
struct ContentView: View {
    var body: some View {
        NavigationView{
            Form{
                Text("hi there")
            }
        }
    }
}
```
![](imgs/nav/nav.png)

```swift
struct ContentView: View {
    var body: some View {
        NavigationView{
            Form{
                Text("hi there")
            }.navigationBarTitle("Nav-title")
        }
    }
}
```
![](imgs/nav/nav-with-title.png)

```swift
struct ContentView: View {
    var body: some View {
        NavigationView{
            Form{
                Text("hi there")
            }.navigationBarTitle("Nav-title", displayMode: .inline)
        }
    }
}
```
![](imgs/nav/nav-inline-title.png)

## State
State make variable become mutable

### Immutable
```swift
struct ContentView: View {
    var body: some View {
        var name = ""
        Form {
            TextField("Enter your name", text: name)
            Text("Hello World")
        }
    }
}
```
![](imgs/state/no-state.png)

### Mutable - two way binding
```swift
struct ContentView: View {
    @State private var name = ""

    var body: some View {
        Form {
            TextField("Enter your name", text: $name)
            Text("Hello World \(name)")
        }
    }
}
```
![](imgs/state/state-binding.png)